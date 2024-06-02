---
Title: DBS101 Flipped Class 12
categories: [DBS101, Flipped_class12]
tags: [DBS101]
---

# Topic: Recovery Algorithms

## Introduction
Recovery algorithms are techniques to ensure database consistency, transaction atomicity, and durability despite failures. There are several other recovery algorithms used in database management systems (DBMS) to ensure data consistency and integrity in the event of failures. In this journal I will focus on log-based recovery, shadow paging and ARIES.

## Log-Based Recovery
The log is a sequence of records. If any operation is performed on the database, then it will be recorded in the log. Log of each transaction is maintained in some stable storage so that if any failure occurs, then it can be recovered from there.

Log-based recovery works by using the transaction log to redo or undo transactions as necessary to bring the database back to a consistent state. When the system crashes, then the system consults the log to find which transactions need to be undone and which need to be redone.

1. If the log contains the record <Ti, Start> and <Ti, Commit> or <Ti, Commit>, then the Transaction Ti needs to be redone.

2. If log contains record<Tn, Start> but does not contain the record either <Ti, commit> or <Ti, abort>, then the Transaction Ti needs to be undone.

<b>Undo and Redo of Transactions</b>

 • undo(Ti) -- restores the value of all data items updated by Ti to their old values, going backwards from the last log record for Ti

- Each time a data item X is restored to its old value V a special log
record <Ti , X, V> is written out

- When undo of a transaction is complete, a log record
<Ti abort> is written out.

• redo(Ti) -- sets the value of all data items updated by Ti to the new
values, going forward from the first log record for Ti
No logging is done in this case

<b>Recovering from Failure</b>

• Transaction Ti needs to be undone if the log
- Contains the record <Ti start>,
- But does not contain either the record <Ti commit> or <Ti abort>.

• Transaction Ti needs to be redone if the log
- Contains the records <Ti start>
- And contains the record <Ti commit> or <Ti abort>

<b>Advantages of Log based Recovery</b>

<b>Durability:</b> In the event of a breakdown, the log file offers a dependable and long-lasting method of recovering data. It guarantees that in the event of a system crash, no committed transaction is lost.

<b>Faster Recovery:</b> Since log-based recovery recovers databases by replaying committed transactions from the log file, it is typically faster than alternative recovery methods.

<b>Incremental Backup:</b> Backups can be made in increments using log-based recovery. Just the changes made since the last backup are kept in the log file, rather than creating a complete backup of the database each time.

<b>Lowers the Risk of Data Corruption:</b> By making sure that all transactions are correctly committed or canceled before they are written to the database, log-based recovery lowers the risk of data corruption.


## Shadow Paging
Shadow paging is a non-log-based recovery mechanism that uses a copy-on-write technique for providing atomicity and durability (two of the ACID properties) in database systems. It is an alternative to log based recovery techniques.

The advantages of shadow paging are as follows;
- No need for log records.
- No undo/ Redo algorithm.
- Recovery is faster.

## Aries
ARIES stands for Algorithm for Recovery and Isolation Exploiting Semantics. It is based on the Write Ahead Log (WAL) protocol, so  any change is recorded in log on stable storage before the database change is written to disk and it must use STEAL + NO-FORCE buffer pool policies. 

Unlike the recovery algorithm described earlier, ARIES uses log sequence number (LSN) to identify log records. There is another key concept in aries; 

- <b>Dirty Page Table (DPT):</b> This table keeps track of pages that have been modified but not yet written to disk. It is crucial during recovery to know which pages were in an unstable state at the time of the crash.

- <b>Transaction Table:</b> This table maintains information about all active transactions at the time of a crash. It helps in determining which transactions need to be rolled back during the recovery process.

The recovery process actually consists of 3 phases:
1. Analysis:
The recovery subsystem determines the earliest log record from which the next pass must start. It also scans the log forward from the checkpoint record to construct a snapshot of what the system looked like at the instant of the crash.
2. Redo:
Starting at the earliest LSN, the log is read forward and each update redone.
3. Undo:
The log is scanned backward and updates corresponding to loser transactions are undone.

## DBloggin
Database logging is a fundamental technique used in DBMS to ensure that all changes made to the database can be traced and, if necessary, reversed. This process is integral to the recovery mechanisms of the system, providing a reliable way to maintain data integrity. 

Database logging is an important part of your highly available database solution design because database logs make it possible to recover from a failure.

## Conclusion
Recovery algorithms are crucial for maintaining data integrity and consistency in database systems. Though there are many recovery algorithms, ARIES is one of the most advanced and widely used algorithms.
