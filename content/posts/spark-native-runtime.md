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

So far, Spark has done almost everything to the SQL optimizer and the performance seems hardly to get a significant improvement like before. So we turned our attention to the runtime, whose performance could be boosted by re-implemented in a native language like C, C++ and Rust.

# How Should We Implement the Spark SQL Native Runtime

## Gluten

## Our In-house Spark SQL Native Runtime