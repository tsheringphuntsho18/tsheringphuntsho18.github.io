---
Title: DBS101 Flipped Class 5
categories: [DBS101, Flipped_class5]
tags: [DBS101]
---

## Topic: Normal Forms

### Introduction
Normal form is a sets of guidelines that is used to design relational databases which are free of data anomalies. Anomalies are irregularities or inconsistencies that occur in a database. In today's flipped class we are grouped in 4 and given 1 type of DBMS normal form to each group, my group got fourth normal form.

### Types of DBMS Normal Form
- First Normal Form
- Second Normal Form
- Third Normal Form
- Boyce-Codd Normal Form
- Fourth Normal Form

### 1. First Normal Form 
This is the most basic level of normalization. In 1NF, each column in th table should be single valued, should have a unique name and the valued stored must be of the same type. The first normal form helps to eliminate duplicate data and simplify queries.

Lets create a table to store student data.

![nf](pictures/1NF.png)

The above table is in first normal form as it fulfills all the criteria of first normal form.

### 2. Second normal form
The 1NF only eliminates repeating groups, not redundancy. That's why there is 2NF. To Be in second normal form, a table should already be in first normal form and relation should not have any partial dependency. That is, all non-key attributes are fully dependent on a primary key. Let's change the student data table to 2NF. We will break down the table into two separate tables to achieve this:

Student table

![nf](pictures/2NFstd.png)

Department table 

![nf](pictures/2NFdep.png)

If there are 100 students in SWE, we don't need to store its department name as SWE for all the 100 records, instead we can store it in the second table as the department_id for SWE is 101.

### 3. Third normal form
A relation is said to be in third normal form, if it satisfies the first normal form and the second normal form and doesn't have transitive dependency. If a column that is not the primary key depends on another column that is also not a primary key then we have Transitive dependency in our table. To resolve transitive dependencies, you would typically split the table into multiple tables to ensure that each attribute is fully functionally dependent on the primary key.
Example;
Student table

![nf](pictures/3NFs.png)

Department table

![nf](pictures/3NFd.png)

Student_department table

![nf](pictures/3NFsd.png)

The student table contains information about students, with student_ID as the primary key. The Department Table contains information about the department with Deparment_ID as the primary key.

The student_deparment Table serves as a linking table to establish the many-to-many relationship between students and departments. Each record in this table represents a student of a particular department.

### 4. Boyce-codd normal form
The Boyce and Codd Normal Form is a higher version of the Third Normal Form. It is also known as 3.5 Normal Form. For a table to be in boyce-codd normal form, the table must be in third normal form and for any dependency A → B, A should be a super key. Which means A cannot be a non-prime attribute, if B is a prime attribute.

### 5. Fourth normal form
For a table to satisfy the fourth normal form,  it should be in the Boyce-Codd normal form and the table should not have any multi-valued dependency. Let's imagine you have a collection of toys, and you want to organize them neatly. In the world of databases, organizing data is like organizing toys. So, fourth normal form is like organizing toys (or data) in a way that makes it easy to find what you need, doesn't waste space by repeating things, and keeps everything tidy and together.

Pair of toys

![nf](pictures/4NF1.png)

To bring it into 4NF

![nf](pictures/4NF2.png)

Now this relation satisfies the fourth normal form.

### Conclusion
Today's flipped class is also the previous one, in which we are divided into groups and discussed on assigned topics. Sometimes time is not efficient for the discussion whereby we need to browse more and deeper so i suggest allocating time according to the content. In this flipped class we didn’t get time to discuss among ourselves because though our topic is fourth normal form, we also need to understand 1NF, 2NF, 3NF and boyce-codd normal. But luckily our group members were sincere and browsed on 4NF and we did presentations up to the college level.

