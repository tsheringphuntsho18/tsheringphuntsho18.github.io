---
Title: DBS101 Flipped Class 7
categories: [DBS101, Flipped_class7]
tags: [DBS101]
---

## Topic : Summary on storage and buffer management

The provided guided session’s code stimulates disk block, RAID configurations and buffer pools.

### Task 1: Disk block implementation

Disk block implementation  simulates a disk with a fixed number of blocks and a fixed block size. It provides methods for allocating, reading, writing, deallocating, and defragmenting blocks of data on the disk. The allocate method allocates contiguous blocks for a given data, and the read, write, and deallocate methods perform the respective operations on the allocated blocks. The defragment method consolidates the allocated blocks to eliminate fragmentation.

The code given in task 1 is an implementation of a disk block with 10 blocks of size 512 bytes . Where a contiguous block for data1 has been allocated and read/write data to those blocks. Then after deallocating data1, new blocks for data3 have been allocated. Finally the disk has been defragmented, which consolidates the allocated blocks for data3.

### Task 2:
RAID configuration simulates different RAID levels(0, 1 and 5) using a fixed block size and configurable numbers of disk. The read and write methods handle data striping(RAID 0), mirroring(RAID 1), and parity(RAID 5) configurations. 

The code given in task 2 is an implementation of a RAID configuration with RAIDarray of 4 disks, block size 512 bytes, and RAID level 0 (striping). Then read it back the data written to the RAIDarray 0. And does the same for RAID 1 whereby it simulates a disk failure, and rebuilds the array using the spare disk.

### Task 3: Buffer pool management
A database buffer pool is a cache in a database management system (DBMS) that stores database pages in memory, allowing quicker access to frequently accessed data.<br>
The implementation demonstrates how to initialize a buffer pool, fetch pages, and manage the buffer pool size by evicting the least recently used page when the buffer is full.


