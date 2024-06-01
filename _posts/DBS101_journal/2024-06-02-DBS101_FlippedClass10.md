---
Title: DBS101 Flipped Class 10
categories: [DBS101, Flipped_class10]
tags: [DBS101]
---
# Transaction and Serializability

## Transaction

A transaction is a single logical unit of work which accesses and modifies the contents of a database. Transactions access data using read and write operations. In order to maintain consistency in a database, before and after the transaction, certain properties called ACID properties.

![transaction](/pictures/DBS_pictures/tacid10.png)

### A Simple Transaction Model

Let’s do a sample transaction in Postgresql. Here I have created a database called test_transaction and inserted sample data in the table accounts.

![transaction](/pictures/DBS_pictures/tra1.png)

![transaction](/pictures/DBS_pictures/tra2.png)

### Transaction Atomicity and Durability

![transaction](/pictures/DBS_pictures/tra3.png)

![transaction](/pictures/DBS_pictures/tra4.png)

### Transaction Isolation

![transaction](/pictures/DBS_pictures/tra5.png)

## Serializability

Serializability is a way to check if the execution of two or more transactions are maintaining the database consistency or not. Serializability is Important as it ensures isolation property of transactions

### Types of Serializability in DBMS

There are two types of serializability; conflict serializability and view serializability.

#### Conflict Serializability

Conflict serializability refers to a subset of serializability that focuses on maintaining the consistency of a database while ensuring that identical data items are executed in an order.
 
#### View Serializability

View serializability is a kind of operation in a serializable in which each transaction should provide some results, and these outcomes are the output of properly sequentially executing the data item.

### Testing of Serializability

To test the serializability of a schedule, we can use Serialization Graph or Precedence Graph. A serialization Graph is nothing but a Directed Graph of the entire transactions of a schedule.

![transaction](/pictures/DBS_pictures/sertye.png)

## Conclusion

As I conclude my journal, I want to mention that the concept of a transaction has been applied broadly in database systems and applications. I have also done a short practical transaction to get hand on practice on how transaction works. DBMS transactions must follow the ACID properties to be considered serializable. There are different types of serializability in DBMS, each with its own benefits and drawbacks. In most cases, selecting the right type of serializability will come down to a trade-off between performance and correctness.
