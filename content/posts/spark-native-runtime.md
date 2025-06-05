---
title: "Thoughts on Spark SQL Native Runtime"
date: "2023-09-22"
categories: "SQL Engine"
tags: ["DBMS", "Data Lakehouse", "Spark SQL"]
draft: true
---

# Why We Need a Native Runtime for Spark SQL

Core parts of Spark SQL
- Parser
- Optimizer
- Executor

Of course, to improvement the performance, we need to start from the optimizer. Spark SQL optimizer is responsible for RBO(rule-based optimization) and CBO(cost-based optimization). There's limited improvement room for RBO since there are just some fixed optimization rules and they are not so adaptive to the dynamic and varied nature of data. That's why CBO has been introduced to help Spark choose better plans by collecting and leveraging various data statistics.

So far, the Spark community has done almost everything to the SQL optimizer and the performance seems hardly to get a significant improvement like before. So we turned our attention to the runtime, whose performance could be boosted by a native runtim in C, C++ or Rust.

# Different Approaches of Spark SQL Native Runtime

## Gluten

Here's a quote from [**the Gluten official site**](https://gluten.apache.org/#12-glutens-solution)

> “Gluten” is Latin for glue. The main goal of Gluten project is to “glue” native libraries with SparkSQL. Thus, we can benefit from high scalability of Spark SQL framework and high performance of native libraries.
>
> The basic rule of Gluten’s design is that we would reuse spark’s whole control flow and as many JVM code as possible but offload the compute-intensive data processing part to native code. Here is what Gluten does:
>
> - Transform Spark’s whole stage physical plan to Substrait plan and send to native
> - Offload performance-critical data processing to native library
> - Define clear JNI interfaces for native libraries
> - Switch available native backends easily
> - Reuse Spark’s distributed control flow
> - Manage data sharing between JVM and native
> - Extensible to support more native accelerators

So the point is that they are focusing on the performance-critical part while reusing most of the JVM code, which is a cost-effective approach. With this apporach we just need to re-implement the data-processing of each task in a native language.

## Native Runtime in Databricks Photon Engine

Here's a quote from [**the Databricks official site**](https://www.databricks.com/blog/2020/06/24/introducing-photon-engine.html)

>Photon Engine accelerates the performance of Delta Lake for SQL and data frame workloads through three components: an improved query optimizer, a caching layer that sits between the execution layer and the cloud object storage, and a native vectorized execution engine that’s written in C++.

So Photon's architecture is centered around 3 key components
- **Improved Query Engine**
- **Caching Layer**
- **Native Vectorized Execution Engine**

And the last one is what we concern about in this article -- a native runtime for Spark SQL. We don't get more details about the native runtime in the referenced blog. But we still have the [**paper of Photon**](https://people.eecs.berkeley.edu/~matei/papers/2022/sigmod_photon.pdf).

## Flare

# Comparison

| | Gluten | Photon | Flare |
|---|---|---|---|
| A |
| B |
| C |