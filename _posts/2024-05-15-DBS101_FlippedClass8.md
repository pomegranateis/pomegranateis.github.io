---
Title: DBS101 Flipped Class 8
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

# Topic: Indexing

The flipped class for this day was solely based on learning the different concepts and types as well as each and every functions of indexing. The activity for today was a Q&A quiz competition between the class members.

## What I Did

First things first. We research, discover and discuss with our respective group mates like always. It was important to do this as we had to learn and comprehend and answer the questions we'd be thrown with. It was serious competition.

But we completed our tasks, made very clear with the concept of indexing while learning the types of it. The questions were very direct and worth being competitive of. 

Winners would get the favour of choosing snacks so the air was quite heavy and filled with tensionnnn honestly.

The best part was when the question read,"What is meant by spatial/temporal data?" because it was my group's topic to research on and I got to answer it and get my team a point.

And basically our team won by a neck because it was a draw and we won a penalty match of rock papers scissors.

## What I Learned

![alt text](<../assets/img/dbs/1_GokwxHxq5I-Myy3_ummrtw.png>)

### My topic: Indexing of Spatial and Temporal data

**Spatial-temporal data** indexing involves organizing and optimizing data structures to efficiently store and retrieve information that varies both in space and time.

These are usually active in geographic and temporal attributes such as GPS tracking, weather monitoring etc.

***Techniques***
* quad-trees
* R-trees
* grid-base

*Main function*: They facilitate **quick** retrieval of relevant data points based on spatial proximity and temporal relevance, enabling efficient analysis and querying of complex spatio-temporal datasets.

### Bitmap Indexing

In **bitmap** indexing, each attribute or column in a table is associated with a bitmap, where each bit represents the presence or absence of a particular value in the dataset.

For example, if we have a table of employees and we want to index their departments, we can create a bitmap index where each department is represented by a bit, and for each employee, the corresponding bit for their department is set to 1.

Bitmap indices excel at handling queries involving **conjunctions** (AND) and **disjunctions** (OR) of multiple conditions. 

*Main function*: By performing bitwise operations on the bitmaps, the database engine can quickly identify the rows matching complex conditions without needing to scan the entire dataset.

Bitmap indexing is particularly effective for low-cardinality columns (columns with few distinct values) and is commonly used in data warehousing and decision support systems.

### Buffer indexing 

Buffer indexing **improve** the efficiency of **I/O** operations, especially in scenarios where data transfer between a slower storage medium (like a hard disk) and a faster one (like RAM) is involved.

In buffer indexing, a buffer **(a portion of memory)** acts as a *temporary* storage area for frequently accessed data or data being transferred between different storage mediums. 

The buffer maintains an *index* or a pointer to the location of the data in the slower storage medium.

When data is requested, the system checks the **buffer** first. 

If the data is found in the buffer (a cache hit), it is returned directly, avoiding the slower disk access. If the data is not in the buffer (a cache miss), it is retrieved from the disk and stored in the buffer for future access.

*Main function*: Buffer indexing helps reduce the **latency** of I/O operations by exploiting temporal locality - *the tendency of programs to access the same data repeatedly over a short period.*

By keeping frequently accessed data in memory, buffer indexing *minimizes* the need for expensive disk accesses.

## Conclusion

After learning about different indexing types such as bitmap indexing and buffer indexing from our quiz activity in class, it's clear that indexing is **REALLY VERY** important in optimizing data storage and retrieval in various contexts. 

Bitmap indexing seems particularly useful for databases with *low-cardinality columns*, enabling efficient querying based on multiple conditions. 

On the other hand, buffer indexing enhances the *performance of I/O operations* by leveraging memory buffers to reduce the latency associated with accessing data from slower storage mediums like disks. 

And at the end there is spatio-temporal indexing which focuses on *quick retrieval of data points* based on spatio-temporal relevence.

Understanding these indexing techniques provides valuable insights into how data can be organized and accessed efficiently, which is essential for designing and optimizing database systems and other computing applications.

