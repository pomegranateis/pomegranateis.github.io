---
Title: DBS101 Flipped Class 10
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

# Recovery systems in Database Management Systems 

Recovery systems in DBMS is mainly useful in ensuring data integrity and system reliability in the face of failures or crashes. 

These systems employ various techniques to restore the database to a consistent state, minimizing data loss and preventing inconsistencies. The primary methods include log-based recovery, commit/redo recovery, and checkpoint recovery, among others.


## Log-Based Recovery

Log-based recovery relies on transaction logs that record all changes made to the database, including updates, inserts, and deletes, along with information about each transaction's start and end times. 

![alt text](<../assets/img/dbs/log-based-recovery-in-dbms-thumbnail-1.webp>)

When a failure occurs, the DBMS uses these logs to identify incomplete transactions and perform a series of operations to undo the incomplete transactions and redo the completed ones. 

This process is known as the **redo/undo** recovery algorithm. The redo operation reapplies changes made by completed transactions not yet saved to the database at the time of failure, ensuring all changes are applied. The undo operation reverses the effects of incomplete transactions, restoring the database to a consistent state.

## Commit/Redo Recovery Technique

This technique focuses on reapplying changes made by successfully completed transactions to the database using log records. 

It aims to restore the database to its most recent consistent state by redoing the changes made by transactions that were in progress at the time of failure or error. This approach ensures that the database reflects the final state intended by all committed transactions.


## Atomicity and Durability

Atomicity ensures that either all operations of a transaction are performed or none are, maintaining the integrity of the database. Durability guarantees that once a transaction is committed, its effects are permanent and survive future system failures. 

![alt text](<../assets/img/dbs/1689955135766.jpeg>)

Techniques such as maintaining logs of each transaction and writing them onto stable storage before modifying the database, or using shadow paging where changes are made on volatile memory and later updated to the actual database, support these properties.

## Handling Concurrent Transactions

Modern DBMSs handle concurrent transactions by using checkpoints to manage interleaved logs. This approach simplifies the recovery process by allowing the system to focus on recovering up to the last checkpoint, reducing the complexity of tracking all transactions.

## Checkpoint Recovery

Checkpoint recovery reduces recovery time by periodically saving the state of the database in a checkpoint file. In the event of a failure, the system can use this checkpoint file to restore the database to the most recent consistent state before the failure, instead of processing the entire log to recover the database. This technique significantly speeds up the recovery process.

![alt text](<../assets/img/dbs/recovery-using-checkpoints.webp>)

Checkpoints are pivotal in DBMS for rapid recovery in case of system failures or crashes. They mark the point until which the consistency of transactions is maintained. This mechanism enhances the consistency of the database, especially when multiple transactions are executed concurrently. Checkpoints serve as synchronization points between the database and the transaction log file, preventing unnecessary redo operations by flushing out dirty pages (modified pages) from logs to data files. This process, known as hardening of dirty pages, is crucial for the restoration of the lost state in the event of a system failure. The frequency of checkpoints can affect the speed of recovery; more frequent checkpoints facilitate quicker recovery but may impact performance.

## Fuzzy or Non-Blocking Checkpoints

Fuzzy checkpoints, or *non-blocking checkpoints*, enable transactions to run against the database while the checkpoint is in progress.

Fuzzy checkpoints do not obtain locks, and therefore have a minimal impact on other database activity. Because transactions may modify the database while a checkpoint operation is in progress, the resulting checkpoint file may contain both committed and uncommitted transactions. Furthermore, different portions of the checkpoint image may reflect different points in time. For example, one portion may have been written before a given transaction committed, while another portion was written afterward. The term "fuzzy checkpoint" derives its name from this fuzzy state of the database image.

To recover the database when the checkpoint files were generated from fuzzy checkpoint operations, TimesTen requires the most recent checkpoint file and the transaction log to bring the database into its most recent transaction-consistent state.

## Algorithm for Recovery and Isolation Exploiting Semantics (ARIES)

It operates under the principle of Write-Ahead Logging (WAL), where every update operation generates a log record that is crucial for recovery purposes. 

These log records can be categorized into three types:

* Undo-only log record: Contains only the before-image of the data, allowing for an undo operation to revert to the previous state.
* Redo-only log record: Contains only the after-image of the data, enabling a redo operation to restore the data to its post-update state.
* Undo-redo log record: Contains both the before and after-images of the data, providing flexibility in recovery operations.

![alt text](<../assets/img/dbs/scanned-document.jpg>)

Each log record is assigned a unique, monotonically increasing Log Sequence Number (LSN), and every data page has a page LSN field indicating the LSN of the last update on that page. The WAL protocol mandates that the log record corresponding to an update must reach stable storage before the data page itself is written to disk. To manage performance, log writes are buffered in a log tail in main memory, which is flushed to disk when full. A transaction cannot be considered committed until its commit log record is persisted to disk.

## Recovery in Main Memory Database

MMDB recovery mechanisms must address the volatility of main memory and the need for rapid recovery to ensure data integrity and system availability. Strategies such as efficient logging, effective checkpointing, and optimized reloading schemes are essential. These mechanisms allow MMDBs to offer high throughput and fast response times while mitigating the risks associated with data loss due to system or media failures.