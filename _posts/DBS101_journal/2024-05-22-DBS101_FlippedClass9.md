---
Title: DBS101 Flipped Class 9
categories: [DBS101, Flipped_class9]
tags: [DBS101]
---

# Topic: Query Optimization

## Introduction

Query Optimization is a crucial aspect of database management systems (DBMS) that seeks to determine the most efficient way to execute a given query by considering a variety of query execution strategies. In this flipped class I learned two query processing that is materialized views and advanced topics in query optimization.

## Materialized view

A materialization view is nothing but, it is a query that fetches the data from one or more tables in the database. The query can involve the operations such as joins, filtering, and aggregations.

The materialized view is defined, and the view is created using the CREATE MATERIALIZED VIEW statement in the SQL. The database system executes the query and stores the result set the same as the table-like structure in the database.

Materialized views are created by executing a query against one or more tables in the database. The results of the query are stored as a static dataset in the materialization view.

## Advanced topics in query optimization

There are various topics which lead the query optimization to its advanced level.

### Top-K Optimization
Top-K optimization aims to efficiently find the top K records from a dataset according to a specific order criterion, such as sorting by value or count. 

### Join Minimization
Join minimization is a query optimization technique that seeks to minimize the number of join operations in a query execution plan. By reducing the number of joins, the optimizer can decrease the computational load and improve query performance.

### Optimization of Updates
Optimization of updates focuses on improving the efficiency of update operations (inserts, deletes, updates) in a database. 

### Multi Query Optimization and Shared Scans
Multi-query optimization (MRO) is a technique that combines multiple queries into a single execution plan to improve performance. Shared scans refer to the practice of scanning a table once and using the results for multiple queries, rather than scanning the table separately for each query. 

### Parametric Query Optimization
In the parametric query optimization method, query optimization is performed without specifying its parameter values. The optimizer outputs several optimal plans for different parametric values.

## What we did in Flipped class
We were divided into 4 groups and then assigned 2 topics(materialized view and advanced topics in query optimization) and discussed in our groups. After browsing the internet, we have understood our topics, then we have created  5 trivia questions. And then for another 10 minutes we were grouped into 2 and we combined our questions with theirs and we also prepared for the trivia round. In the trivia round, the 2 groups ask questions alternatively. It was really interesting and i enjoyed it very much.
