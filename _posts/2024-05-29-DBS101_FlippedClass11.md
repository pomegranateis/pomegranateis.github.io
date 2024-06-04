---
Title: DBS101 Flipped Class 11
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

# Locks and Latches

Locks and latches have different scopes and lifecycles. Locks apply to what you might call database physical model elements -- tables, rows, index entries. Latches protect various memory structures the database server uses when executing SQL statements or performing its housekeeping tasks.

## Locks

Locks are used to enforce consistency and isolation in database transactions. They are typically employed to protect database objects such as rows, pages, or entire tables from concurrent modification. Locks can be classified into two primary types:

![alt text](<../assets/img/dbs/Locks-1.webp>)

* Shared Locks: Allow multiple transactions to read (or select) the locked resource concurrently but prevent any transaction from modifying it.

* Exclusive Locks: Grant exclusive access to the locked resource, preventing other transactions from reading or writing to it until the lock is released.

Locks are managed through a lock table, which tracks the status of all locks held by ongoing transactions. The lock manager is responsible for granting and releasing locks according to the rules defined by the isolation level of the database. Deadlocks involving locks are possible and require detection and resolution mechanisms.

Locks are primarily used to ensure logical consistency across transactions and are held for the duration of the transaction that acquires them. This means that locks can significantly impact the performance of a database, especially in environments with high concurrency.

## Latches

Latches, on the other hand, are lightweight synchronization primitives used internally by the DBMS to protect shared resources such as data structures or buffers from concurrent access by multiple threads or processes. Unlike locks, latches are not part of the transaction model and are not managed by a lock manager. Instead, they are used for short periods to synchronize access to low-level database components.

Latches can operate in shared and exclusive modes, similar to locks, but they are typically held for much shorter durations—often just a few CPU cycles. This makes latches highly efficient for protecting frequently accessed data structures within a DBMS.

Key characteristics of latches include:

* Location: Latches reside in memory near the resources they protect, facilitating quick access and release.
* Acquisition Strategy: Latches are acquired by specialized code inside the DBMS, often based on internal logic unrelated to application data access patterns.
* Deadlock Avoidance: Latch deadlocks represent bugs in the DBMS code, emphasizing the importance of careful latch management.
* Hardware Utilization: Latches are implemented using atomic hardware instructions or, in rare cases, mutual exclusion in the operating system kernel.

### Main differences

![alt text](<../assets/img/dbs/images (1).png>)

### Optimization and Considerations

Optimizing the usage of locks and latches is crucial for achieving high performance in a DBMS. Strategies include:

1. Avoiding Single Lock/Latch for Entire Data Structures: Dividing data structures into smaller units can reduce contention and improve concurrency.
2. Prompt Acquisition and Release: Holding locks or latches for extended periods can degrade performance. Efficiently acquiring and releasing these mechanisms is vital.
3. Lock Escalation: Automatically converting fine-grained locks into coarser-grained ones to reduce overhead.

Understanding the role and behavior of locks and latches in a DBMS is essential for database administrators and developers to optimize database performance, manage concurrency effectively, and troubleshoot issues related to data consistency and access contention