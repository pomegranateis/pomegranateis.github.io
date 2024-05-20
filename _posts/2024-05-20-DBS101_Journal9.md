---
Title: DBS101 Flipped Class 9
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

# What i did

The flipped class for today was solely based on learning the different concepts and types as well as each and every functions of **Query Optimisation**. The activity for today was a Q&A quiz competition between the class members. The twist for today was to make the quiz questions ourselves and ask each other the quiz questions.

The class was distributed into two groups each containing a sub-group of students researching on either *materialized views* or *query optimization*

# What i learned

## Materialized Views

![alt text](<../assets/img/dbs/images.png>)

A materialized view is a database object that contains the results of a query. 

Unlike a regular view, which does not store data physically but rather provides a virtual table based on the result set of a SQL statement, a materialized view stores its data physically in the database. 

* This means that it can be queried like a regular table, even when the underlying data changes.

### Advantages

1. Since the data is pre-computed and stored, querying a materialized view can be **faster** than executing the original query, especially if the query involves complex joins or aggregations.

2. They allow you to simplify complex queries by **encapsulating** them within the materialized view definition.

3. Materialized views support partitioning, allowing for more **efficient storage** and retrieval of large datasets.

### Disadvantages

1. Storing the result set of a query consumes disk space.

2. When the underlying data changes, the materialized view needs to be refreshed, which can be resource-intensive depending on the complexity of the query and the size of the dataset.

## Query Optimization

Query optimization is a crucial aspect of DBMS that focuses on improving the efficiency of query execution.

1. Cost-Based Optimization:
In cost-based optimization, the optimizer estimates the cost of different execution plans and chooses the one with the lowest estimated cost. The cost estimation considers factors such as CPU time, I/O operations, and memory usage.

2. Indexes:

![alt text](<../assets/img/dbs/Screenshot from 2024-05-20 23-49-44.png>)

Indexes play a vital role in query optimization. They can significantly speed up data retrieval by reducing the amount of data that needs to be scanned. However, they also have overheads, including storage and maintenance costs.

3. Parallel Execution:
Parallel execution allows multiple parts of a query to be executed simultaneously across multiple processors or cores. This can lead to significant performance improvements for complex queries and large datasets.

4. Caching:
Caching frequently accessed data in memory can drastically reduce query response times. However, managing cache coherence and eviction policies is essential to ensure that the most relevant data is always available.

5. Query Rewriting:
The optimizer may rewrite queries to improve performance. Techniques include predicate pushdown, where conditions are moved closer to the data source, and join reordering, where the order of joins is changed to minimize data shuffling.

6. Statistics and Histograms:
Accurate statistics about the distribution of data in tables and indexes help the optimizer make better decisions. Histograms provide a more detailed view of data distribution compared to simple count statistics.

# Conclusion

Both materialized views and advanced query optimization techniques are powerful tools for enhancing database performance. 

While materialized views offer a way to precompute and store query results for faster access, advanced query optimization strategies focus on improving the efficiency of query execution through various mechanisms. 

Understanding and applying these concepts effectively requires a deep dive into the specific DBMS being used, as different systems may implement these features differently.

