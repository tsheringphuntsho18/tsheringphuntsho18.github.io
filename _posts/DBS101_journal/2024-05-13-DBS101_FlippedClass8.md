---
Title: DBS101 Flipped Class 8
categories: [DBS101, Flipped_class8]
tags: [DBS101]
---

# Topic : Indexing
Indexing is a special lookup table (data structures in document databases) that are used by the database search engine to speed up data retrieval/query. Indexing improves database performance by minimizing the number of disc visits required to fulfill a query.

## Introduction
In this flipped class, we did 3 activities on the topic indexing, leading to a better understanding of a buffer tree and bitmap indices and the indexing of spatial and temporal data. First activity is to discuss the given types of indexing. Second activity was to explain the topic to the members of different groups and finally we had a quiz competition between team A and team B.

### First activity
My group was assigned a buffer tree(one of the types of indexing). Following information is what we have come up with.

![buffertree](/pictures/DBS_pictures/buffertree.png)

A buffer tree is a specialized data structure designed to efficiently manage large datasets stored on external storage devices like hard drives. Buffer trees are built on top of an (a, b)-tree, a balanced search tree structure. This ensures efficient searching and organization within the data.

Whenever a buffer becomes full, its contents are pushed down to the node’s children using a small number of I/Os. The main idea of buffering technique is to perform operations on an external tree data structure in a lazy manner. When inserting an element we do not search down the tree for the relevant leaf right away but wait until we have collected a batch of insertion and then we insert this block into the buffer of the root.

The advantages of buffering is that as a result of laziness, we can have several insertions and deletions of the same elements in the tree at the same time.

### Second activity 
Then we shuffle with the other group members to explain our topics. My group explained to them about buffer trees and the other two groups explained about bitmap indices and  Indexing of Spatial and Temporal Data.

#### Bitmap indices

A bitmap is the combination of two words: bit and map. A bit can be termed as the smallest unit of data in a computer and a map can be termed as a way of organizing things.

Bitmap Indexing is a data indexing technique used in database management systems to improve the performance of read-only queries that involve large datasets. It involves creating a bitmap index, which is a data structure that represents the presence or absence of data values in a table or column. In a bitmap index, each distinct value in a column is assigned a bit vector that represents the presence or absence of that value in each row of the table. The bit vector contains one bit for each row in the table, where a set bit indicates the presence of the corresponding value in the row, and a cleared bit indicates the absence of the value.

#### Indexing of Spatial and Temporal Data.

If data is recorded according to time then it is called temporal data.<br>
Ex: Covid-19 patients after 24-hours

If data is recorded according to location, space or geographical point of view, then it is declared spatial data.<br>
Ex: Covid-19 patient in bhutan, india and china.

### Third activity
Our final activity for the flipped class was the quiz competition between two teams (team A and team B). Each team has members from each topic and each team has 12 members. Following are the quiz questions with answers.

#### Round one (MCQ)
1. The buffer tree is an alternative approach to the _______.<br>
ANS: Log-structured merge tree.

2. In a buffer tree a buffer is associated with each ___node of a b+ tree.<br>
ANS: internal

3. When an index record is inserted into the buffer tree, it is first inserted into the buffer of the ____ node.<br>
ANS: root

4. Bitmap indices are designed for easy querying on ____ keys.<br>
ANS: multiple

5. Buffer trees have been implemented as a part of the ___________ index structure in postgresQL.<br>
ANS: Generalized search tree

6. In a bitmap index, each bitmap has as many bits as the ____ of records in the relation.<br>
ANS: number

7. Bitmap indexes are useful for selections mainly when there are selections on ___keys.<br>
ANS: multiple

8. The ___ of two bitmaps is computed to answer queries on multiple keys using bitmap indices.<br>
ANS: intersection

9. On SSD storage, buffer trees can provide better write performance compared to LSM trees.(True/False)<br>
ANS: True

10. Temporal data refers to data that has an associated time period. (True/False)<br>
ANS: True


Round two (Rapid answer questions)[10 marks]
1. Important of indexing.
- Improved Search Performance
- Enhanced Data Retrieval
- Optimized Query Processing
- Support for Complex Queries
- Reduced Resource Consumption
- Scalability
- Optimized Storage
- Consistency and Reliability
- Facilitates Sorting and Filtering
- Supports Data Integrity Constraints

2. Types of indexing.
- B-Tree Indexing
- Hash Indexing
- Inverted Indexing
- Bitmap Indexing
- Spatial Indexing
- Full-text Indexing
- Clustered Indexing
- Non-clustered Indexing
- Primary indexing
- Secondary indexing


![quiz](/pictures/DBS_pictures/quiz.jpg)

## Conclusion
By doing these 3 activities, I have gained much knowledge on the topic indexing and the types of indexing. The class was so interesting and interactive that all the students has fully engaged in the group discussion.
Both teams end up in the tie, so winner of the quiz was decided by playing rock paper scissors and team A won it.
