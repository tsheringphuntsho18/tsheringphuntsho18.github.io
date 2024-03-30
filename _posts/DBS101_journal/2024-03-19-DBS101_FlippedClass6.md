---
Title: DBS101 Flipped Class 6
categories: [DBS101, Flipped_class6]
tags: [DBS101]
---

## Topic: Types of Nonrelational databases
### Introduction
NoSQL is a non-relational database that is used to store the data in the non tabular form. NoSQL stands for Not only SQL. During the flipped class we are divided into 6 groups and given types of non relational databases each to the group and I am in group 6 and got column oriented databases.

### Types of NoSQL Database:
- Document based databases
- Key-Value based databases
- Graph Databases
- Vector Databases
- Time-series Databases
- Column oriented Databases 

#### 1. Document based databases
The document based database is a nonrelational database. Instead of storing the data in tables, it uses the documents to store the data in the database. These documents can be in various formats like JSON(javaScript Object Notation), BSON (Binary JSON), XML (eXtensible Markup Language).

#### Advantages
Documents in the database have a flexible schema. It means the documents in the database need not be the same schema. The creation of documents is easy and minimal maintenance is required once we create the document.

#### Disadvantages
It can lead to data duplication across documents. 

#### Application
It use for both transactional and analytical applications like;
Payment processing
Customer data management

#### 2. Key value based databases
Key value based database is a non relational database which simply stores data in key-value pairs. The data can be retrieved by using a unique key allotted to each element in the database. The values can be simple data types like strings and numbers or complex objects.

![dbs](/assets/DBS_pictures/kv.png)

A key-value store is like a relational database with only two columns which is the key and the value.

#### Advantage 
It is easy to understand, use, and manage data.

#### Disadvantages
Modeling complex relationships between data entities can be challenging in key-value databases

#### Application
key-value databases are used to store user profiles in e-commerce platforms and social media. 


#### 3. Graph databases
Graph database uses graphs to store the data in the form of nodes in the database. The connections between the nodes are called links or relationships. graph databases store data as a network of entities and relationships. As a result, these databases often provide better performance and flexibility as they are more suited for modeling real-world scenarios.

![dbs](/assets/DBS_pictures/graph.png)


The above graph shows an example of a social network graph. Given the people (nodes) and their relationships (edges), you can find out who the "friends of friends" of a particular person are—for example, the friends of Norbu Dendup's friends.

#### Advantage
It is easy to identify the relationship between the data by using the links and Updating data is also easy.

#### Disadvantages
Designing and modeling data in a graph database can be complex compared to relational databases. 

#### Application 
Graph databases are widely used to model and analyze social networks, enabling features such as friend recommendations, social graph analysis, and content personalization.


### 4. Vector Databases
It is a database that stores and manages data in vector form. A vector is a list of numbers, like: {12, 13, 19, 8, 9}. These numbers indicate a location within a space. Vector databases first convert data into vectors and create indexing for faster searching. Vectors are often used to represent various types of data, such as numerical values, text, images, or any other data that can be represented as a set of attributes or features.

![vector](/assets/DBS_pictures/vector.png)

#### Advantage 
Vector databases work at scale, work quickly, and are more cost-effective.

#### Disadvantage
It is challenging to interpret the underlying reason behind those relationships as vector databases don’t explain the model's interpretability.

#### Application
It is used in machine learning and deep learning. The ability to connect relevant items of information makes it possible to construct machine learning and deep learning models that can do complex cognitive tasks.

#### 5. Time-series Databases
A time-series database is a database system designed to store and retrieve time-series data. Time-series data is simply data with a timestamp collected with the intent of tracking changes over time.

#### Advantage
Time series databases are optimized for storing large volumes of time-stamped data efficiently.

#### Disadvantage
Time series databases are optimized for time series data and it’s  not suitable for other types of data or general-purpose use cases.

#### Application
Time series databases are commonly used in monitoring and alerting systems to collect, store, and analyze metrics and events from various sources such as servers, networks, and applications.

#### 6. Column oriented Databases 
A column-oriented database is a non-relational database that stores the data in columns instead of rows. Column-oriented databases, also known as columnar databases.

Imagine if you have a box of colored pencils. Instead of mixing all the colors together, you decide to keep all the same colored pencils together. So, all the blue pencils are in one container, all the red pencils in another container and so on. This is what a columnar database does. It keeps all similar information together in one 'column', making it easier to find and use.

![dbs](/assets/DBS_pictures/columnar.png)

#### Advantages
Think of columnar databases like a well-organized toy box. When you want to play with a certain type of toy, like all the cars or all dolls, you can easily find them because they're all stored together. This makes it super fast to find and play with your favorite toys.
This allows for faster query processing, especially when dealing with large datasets.


#### Disadvantages
However, if you want to play with a mix of toys, like a  car, a doll, and a dinosaur, it can take a little longer because you have to go to each separate section to get them.
Modifying and deleting data is slower and more complex compared to row-oriented databases

#### Application
Columnar database is used in various Blogging Platforms and It is used in Content management systems like WordPress, Joomla, etc.

### Conclusion
There are different types of Nonrelational databases also known as NoSQL databases and different types of NoSQL have different advantages, disadvantages and applications. During this flipped class, my group  discussed columnar databases and others on the type of Nonrelational database that they are assigned with. But this time we did not have to present in the class, instead we again mixed with other group members and formed a new group where one member from each group is present to explain their topic. So in this new group we explained our topic and after that we had question and answer session with the whole class.  

