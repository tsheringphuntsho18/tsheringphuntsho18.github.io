---
Title: DBS101 Flipped Class 11
categories: [DBS101, Flipped_class11]
tags: [DBS101]
---

# Topic: Concurrency Control
Concurrency control is a very important concept of DBMS which ensures the simultaneous execution or manipulation of data by several processes or users without resulting in data inconsistency. For maintaining the concurrency of the database, we have the concurrency control protocols.

## Two-phase locking
A transaction is said to follow the Two-Phase Locking protocol if Locking and Unlocking can be done in two phases. The 2 phase are; 

1. Growing Phase: New locks on data items may be acquired but none can be released.

2. Shrinking Phase: Existing locks may be released but no new locks can be acquired.

If lock conversion is allowed, then upgrading of lock( from S(a) to X(a) ) is allowed in the Growing Phase, and downgrading of lock (from X(a) to S(a)) must be done in the shrinking phase.

## Timestamp ordering concurrency control
The Timestamp Ordering Protocol is used to order the transactions based on their Timestamps. The timestamp ordering protocol maintains the timestamp of last 'read' and 'write' operation on a data. 

This is the responsibility of the protocol system that the conflicting pair of tasks should be executed according to the timestamp values of the transactions.

- The timestamp of transaction Ti is denoted as TS(Ti).
- Read time-stamp of data-item X is denoted by R-timestamp(X).
- Write time-stamp of data-item X is denoted by W-timestamp(X).

## Locks VS Latches
![VS](/pictures/DBS_pictures/lvsl.png)

