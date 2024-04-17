---
title: Enoch's CV
ShowToc: true
---

## ABOUT

- Enoch Tsao - **Software Engineer (C/C++)**
- [enoch.tsao@outlook.com](mailto:enoch.tsao@outlook.com)

### Summary

Enoch is a software engineer with skills of system programming and data engineering. In chronological order, Enoch has programmed in C, Java, Scala and C++, which was not determined by his personal preferences, but by the needs of various projects. Eventually he realized that C++ was his favorite language, so he decided to focus on C++ programming.

Enoch is especially good at

- Addressing tricky issues such as troubleshooting/fixing weird bugs and implementing complex features independently
- Mastering new skills quickly. For example, Enoch is able to become productive in a new programming language within 2 weeks
- Writing clear and concise documents so that his teammates and customers will get things done smoothly

---

## CORE SKILLS

Enoch's skill levels are decribed from low to high with terms of **Basic / Intermediate / Advanced / Expert**.

### Programming Languages

- Java / Scala (Advanced)
- C / C++ (Advanced)

### Frameworks / Tools

- Spark SQL (Advanced)
- Arrow (Intermediate)

### Domains

- Query Engine (Advanced)
- Data Engineering (Advanced)

---

## EXPERIENCE

### Freelance Software Engineer (06/2018 - Present)

- **Windjammer Tech in CA, USA (06/2018 - Present, Remote)**
  - Enoch is working on the Windjammer Query Engine in C/C++ and Java/Scala
- Besides working for Windjammer Tech, Enoch has created his own products including
  - **Yunmo Smarthome (06/2021 - 06/2022)** - A smarthome system for hotels
  - **HIFT (10/2022 - 08/2023)** - An e-commerce platform for freelance fitness trainers and fitness enthusiasts
- Also, Enoch contributed a few patches to [TiDB](https://github.com/pingcap/tidb) on 2020 just for a better understanding of how DBMS works

### Software Engineer (03/2013 - 06/2018)

During these years, Enoch has built data platforms based on the Apache Spark ecosystem for the following companies

- **eBay in Shanghai, China (04/2018 - 06/2018)**
- **GrowingIO in Beijing, China (Aug 2016 - Feb 2018)**
- **Westen Bridge Tech in Nanjing, China (Mar 2013 - Aug 2016)**


---

## MAJOR PROJECTS

### Windjammer Query Engine (06/2018 - Present)

The goal of the project is to implement another execution engine in C/C++ for Spark SQL to meet the scenarios of ad-hoc queries, which needs to be significantly faster than the default Spark SQL execution. We reused the parser and optimizer of Spark SQL and integrated them with the native execution. The native execution is based on the MPP model. So it is completely different from the default Spark SQL execution, which is based on the MapReduce model.

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
