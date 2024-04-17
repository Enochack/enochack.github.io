---
title: Enoch's CV
ShowToc: true
---

## PROFILE

- [enoch.tsao@outlook.com](mailto:enoch.tsao@outlook.com)
- B.S. / Optical Information Science / Nanjing University of Information Science and Technology (Feb 2008 - Jun 2012)

---

## SUMMARY

Enoch is a software engineer with skills of system programming and data engineering. He is especially good at

- Addressing tricky and complex issues
- Mastering new skills quickly, not limited to technical skills
- Writing clear and concise documents

Here is an overview of Enoch's experience

- [Jun 2018 - present] A freelancer with diverse skills, including
  - Developing SQL engines for OLAP in C/C++
  - Developing mobile/web applications based on Spring Boot and Vue.js
  - Writing PRD and drawing wireframes with Lark
- [Mar 2013 - Jun 2018] A full-time engineer building OLAP platforms based on the Spark ecosystem for 3 companies

In chronological order, Enoch has programmed in C, Java, Scala, C++, which was not determined by his personal preferences, but by the needs of various projects. Eventually he realized that C++ was his favorite language, so he decided to focus on C++ programming.

---

## CORE SKILLS

### Programming Languages

- Java / Scala (Expert)
- C / C++ (Advanced)

### Frameworks / Tools

- Spark SQL (Expert)
- Arrow (Proficient)

### Domains

- Query engine (Expert)
- Data engineering (Expert)

---

## EXPERIENCE

### Freelancing (06/2018 - Present)

As a freelancer, Enoch is mainly working on a query engine project. In the spare time, he also tried creating his own products including

- A smarthome system for hotels
- An e-commerce platform for freelance fitness trainers and fitness enthusiasts

### Windjammer Tech - California, USA (Remote / Freelance, 06/2018 - Present)

A startup focusing on OLAP query engine.

#### Query Engine Engineer

- Built a distributed query Engine in C/C++

### eBay - Shanghai, China (04/2018 - 06/2018)

An American multinational e-commerce company.

#### Senior Software Engineer

- Built the data platform for user behavior and traffic analytics based on the Apache Spark ecosystem
- **Enoch left eBay two months after starting there due to some unexpected personal issues that required him to work from home**

### GrowingIO - Beijing, China (Aug 2016 - Feb 2018)

A startup that has developed a benchmark-level user behavior analytics platform.

#### Senior Data Engineer

- Built the data platform for user behavior analytics based on the Apache Spark ecosystem and AWS

### Westen Bridge Tech - Nanjing, China (Mar 2013 - Aug 2016)

A startup developing on-premises user behavior analytics platforms.

#### Data Engineer

- Built the data platform for user behavior analytics based on the Apache Spark ecosystem

---

## MAJOR PROJECTS

### Windjammer Query Engine (06/2018 - Present)

The goal of the project is to implement another execution engine in C/C++ for Spark SQL to meet the scenarios of ad-hoc queries, which needs to be significantly faster than the default Spark SQL execution.

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

### GrowingIO (Aug 2016 - Feb 2018)

A SaaS platform for analyzing user behavior in different dimensions. The platform ingests **over 100 billions (about 50TB)** actions and analyzes **tens of billions (about 10TB)** actions every single day.

- Tech stack
  - Scala / Java
  - Spark / HBase / Elasticsearch / Kafka
- Enoch's contributions
  - 90%+ of the ad-hoc queries respond **within 2 seconds**
  - Reduced the duration of some Spark jobs **from minutes to seconds**
  - Compressed the data stored in HBase by **50%+** with a special data structure

