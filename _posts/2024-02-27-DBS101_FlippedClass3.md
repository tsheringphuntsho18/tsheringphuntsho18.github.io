---
Title: DBS101 Flipped Class 3
categories: [DBS101, Flipped_class3]
tags: [DBS101]
---

## Topic: Null values and Set operations in SQL

In this flipped class i learned about Null values and set operations in SQL. As usual flipped calss was every enjoyable learning with friends. Discussing with friends and browsing through internet, we understand about null values and set operations in SQL.

### Null values in SQL
In SQL there may be some records in a table that do not have values or data for every field and those fields are termed as a null value. A null value is different from a zero value or a field that contains spaces. A field with a null value is one that has been left blank during record creation. Null values could be possible because at the time of data entry, information is not available.  Each null value is considered to be different from every other null value in the database.

#### How to test for Null values
SQL allows queries that check whether the value is null. It is not possible to test for null values with comparison operators, such as =, <, or <>. So to check whether the values is null or not we have to use IS NULL and IS NOT NULL operators. For an example;

![null value](pictures/ss9.png)

### Set operations in SQL
Set operators are special type of operators which are used to combine the result of two queries. Operators covered under SET operators are: Operators covered under set operators are union, union all, intersect and minus.
![type](pictures/ss10.png)

#### Union
Union operation is used to combine the result of two or more sql queries into a single table of all matching rows. The union operation eliminates the duplicate rows from its resultset. For an example, there are two query set 1 and set 2 as shown below.

![union](pictures/ss11.png)

The resultset table will look like this:


![unires](pictures/ss15.png)

#### Union All
Union All operation is equal to the Union operation. It returns the set without removing duplication and sorting the data. Example;

![unionall](pictures/ss13.png)

The resultset table will look like this:


![unialres](pictures/ss17.png)

#### Intersect
The intersect operation returns the common rows from both the SELECT statements. Example;

![intersect](pictures/ss12.png)

The resultset table will look like this:


![intersectres](pictures/ss16.png)

#### Minus
Minus operator is used to display the rows which are present in the first query but absent in the second query.

![minus](pictures/ss14.png)

The resultset table will look like this:


![minusres](pictures/ss18.png)


It was a hot discussion between my group mates. The class was divideed into groups home group and given a topic, our group got set operators. We browsed through the internet and made ourselve 100% confident with what we are going to talk about when we are again divided into expert groups. My friends were explaining null values with real world examples and they answered all my questions and cleared the doubts that I had. Then my turn came to explain about the set operators. I also did my part very well that my friend has a good knowledge about set operators. By the way, it was just a piece of cake to me. In our flipped classroom, students taking charge of their learning makes it feel more personal and interactive. It is making students responsible for their education.





