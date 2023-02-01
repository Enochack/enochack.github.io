---
title: "Manage Your Java Application with Systemd"
date: "2023-01-26"
categories: Tech
tags: ["Linux", "systemd", "Java"]
---

## What is Systemd

Refer to https://www.freedesktop.org/wiki/Software/systemd/

> `systemd` is a suite of basic building blocks for a Linux  system. It provides a system and service manager that runs as PID 1 and  starts the rest of the system. `systemd` provides aggressive  parallelization capabilities, uses socket and D-Bus activation for  starting services, offers on-demand starting of daemons, keeps track of  processes using Linux control groups, maintains mount and automount  points, and implements an elaborate transactional dependency-based  service control logic. `systemd` supports SysV and LSB init  scripts and works as a replacement for sysvinit. Other parts include a  logging daemon, utilities to control basic system configuration like the hostname, date, locale, maintain a list of logged-in users and running  containers and virtual machines, system accounts, runtime directories  and settings, and daemons to manage simple network configuration,  network time synchronization, log forwarding, and name resolution. See  the introductory [blog story](http://0pointer.de/blog/projects/systemd.html) and [three](http://0pointer.de/blog/projects/systemd-update.html) [status](http://0pointer.de/blog/projects/systemd-update-2.html) [updates](http://0pointer.de/blog/projects/systemd-update-3.html) for a longer introduction. Also see the [Wikipedia article](http://en.wikipedia.org/wiki/Systemd).

## Why Systemd

We choose `systemd` to manage the Java application since it

- keeps track of processes using Linux control groups
- implements an elaborate transactional dependency-based service control logic
- automates process restarts
- uses simple and clear service configuration
- has become a standard part of mainstream Linux distro

## How to Use Systemd to Manage a Java Application

### 1. Write the startup script

```bash
#!/usr/bin/env bash

BASE_DIR=$(cd $(dirname $0)/..; pwd)

JAVA="/path/to/java"

# Use exec to reuse the current process ID
# Or you will need to store the Java process ID to a file
# And provide the path to the Java pid file in the service file
exec ${JAVA} \
  -jar ${BASE_DIR}/jars/app.jar \
  >> ${BASE_DIR}/log/app.log \
  2>&1
```

In fact, you could also provide the Java command as the `ExecStart` parameter value in the service file instead of writing a script. e.g.

```ini
ExecStart=/path/to/java -jar /path/to/jar
```

Personally, I prefer to use a script since the Java parameters need to be modified at times and I don't think it's a good idea to do such modifications in the service file.
The script redirects the `stdout` and `stderr` to a log file. There is another choice -- managing log with `journald`, which is introduced with `systemd`. If you prefer the `journald` way, just don't redirect `stdout` or `stderr` and `journald` will handle all output well. Here's the reference of `journald` https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html.

### 2. Write the `systemd` service file and named it as `app.service`

```ini
[Unit]
Description=The Application Server
After=syslog.target network.target nss-lookup.target
StartLimitIntervalSec=300
StartLimitBurst=5

[Service]
User=test
Type=simple

# Allow normal process to bind to privileged port
CapabilityBoundingSet=CAP_NET_BIND_SERVICE
AmbientCapabilities=CAP_NET_BIND_SERVICE
NoNewPrivileges=true

# Automatic restarts
ExecStart=/path/to/startup/script
Restart=on-failure
RestartSec=2

[Install]
WantedBy=multi-user.target
```

### 3. Copy/move the systemd service file to `/etc/systemd/system/` as root

```bash
cp /path/to/service/file /etc/systemd/system/
```

### 4. Enable & start the service as root

```bash
systemctl enable app
systemctl start app
```

### 5. Check the status of the service

```bash
systemctl status app
```

If the service was started successfully, the output should be like this
```bash
● app.service - The Application Server
     Loaded: loaded (/etc/systemd/system/app.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-01-26 19:04:39 CST; 32min ago
   Main PID: 54184 (java)
      Tasks: 57 (limit: 8668)
     Memory: 1.7G
        CPU: 1min 7.527s
     CGroup: /system.slice/app.service
             └─54184 /usr/bin/java -jar /path/to/jar>

Jan 26 19:04:39 stage-01 systemd[1]: Started The Application Server.
```

## How to Stop / Restart the service

### Commands

```bash
# stop
systemctl stop app
# restart
systemctl restart app
```

### How Systemd stop services by default

Refer to https://www.freedesktop.org/software/systemd/man/systemd.kill.html

> Processes will first be terminated via `SIGTERM` (unless the signal to send is changed via `KillSignal=` or `RestartKillSignal=`). Optionally, this is immediately followed by a `SIGHUP` (if enabled with `SendSIGHUP=`). If processes still remain after:
>
> - the main process of a unit has exited (applies to `KillMode=`: `mixed`)
> - the delay configured via the `TimeoutStopSec=` has passed (applies to `KillMode=`: `control-group`, `mixed`,              `process`)
>
> the termination request is repeated with the `SIGKILL` signal or the signal specified via `FinalKillSignal=` (unless this is disabled via the `SendSIGKILL=` option). 

So if you didn't specify an `ExecStop` parameter in the service file, Systemd has the default way to stop the service. Of course, the default way is good enough in most cases.