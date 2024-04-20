---
title: Enoch's CV
ShowToc: true
---

## ABOUT

- Enoch Tsao - **Software Engineer (C/C++)**
- [enoch.tsao@outlook.com](mailto:enoch.tsao@outlook.com)

### Summary

Enoch is a software engineer with backgrouds of **SQL Engine** and **Data Engineering**.

- As Enoch has worked on a [**SQL engine**](#windjammer-query-engine-062018---present) in **C/C++**, he has developed skills of
  - **System Programming in C/C++ (Advanced)**
  - **SQL Engine (Advanced)**
  - **Arrow (Intermediate)**
- As Enoch has worked on a large scale [**data platform**](https://www.growingio.com) in **Java/Scala/SQL**, he has developed skills of
  - **Object Oriented Programming (Advanced)**
  - **Functional Programming (Advanced)**
  - **SQL for analytics (Advanced)**
  - **Data Engineering based on the Apache Spark ecosystem (Advanced)**
- As Enoch has worked on above challenging projects, he becomes able to addressing tricky issues such as weird bugs and complex features independently
- Eventually Enoch realized that **Modern C++** was his favorite language, so he decided to focus on **Modern C++** programming

---

## EXPERIENCE

### Freelance Software Engineer (06/2018 - Present)

- **Windjammer Tech in CA, USA (06/2018 - Present / Remote / Part-time)**
  - Enoch is working on the Windjammer Query Engine in **C/C++** and **Java/Scala**
- Besides working for **Windjammer Tech**, Enoch has created his own products including
  - **Yunmo Smarthome (06/2021 - 06/2022)** - A smarthome system for hotels
  - **HIFT (10/2022 - 08/2023)** - An e-commerce platform for freelance fitness trainers and fitness enthusiasts
- Also, Enoch contributed a few patches to [**TiDB**](https://github.com/pingcap/tidb) on 2020 just for a better understanding of how DBMS works

### Software Engineer (03/2013 - 06/2018)

During these years, Enoch was building data platforms based on the Apache Spark ecosystem for the following companies

- **eBay in Shanghai, China (04/2018 - 06/2018)**
- **GrowingIO in Beijing, China (Aug 2016 - Feb 2018)**
- **Westen Bridge Tech in Nanjing, China (Mar 2013 - Aug 2016)**


---

## MAJOR PROJECTS

### Windjammer Query Engine (06/2018 - Present)

The goal of the project is to implement another execution engine in C/C++ for Spark SQL to meet the scenario of ad-hoc querying, which needs to be significantly faster than the default Spark SQL execution. We reused the parser and optimizer of Spark SQL and integrated them with the native execution. The native execution is based on the MPP model. So it is completely different from the default Spark SQL execution, which is based on the MapReduce model.

- Partly refer to the paper of [Flare](https://www.cs.purdue.edu/homes/rompf/papers/essertel-osdi18.pdf)

- Tech stack

  - C / C++ / Java /Scala
  - Spark / Arrow

- Enoch's contributions

  - Participating in the design of the architecture
  - Designing and implementing executors of file-writer/file-reader / hash-join / hash-aggregate
  - Designing and implementing features of dynamic-partition-pruning / monitoring
  - Designing and implementing the local cache of AWS S3/Google FS data to accelerate the reading of hot data
  - Designing and implementing the file-index to reduce unnecessary file-scans
  - Based on the TPCDS-2.4 benchmark, the performance improvement compared to Spark SQL is up to **~4x**, on average **~2x**

---

## EDUCATION

### Nanjing University of Information Science and Technology (09/2008 - 06/2012)

- Bachelor of Science in Optical Information Science & Technology
