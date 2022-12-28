# Databases Basics

A database is a collection of data that is organized and stored in a structured way.

There are many different types of databases, including:
* Relational databases (such as MySQL and PostgreSQL)
* NoSQL databases (such as MongoDB and Cassandra)
* In-memory databases (such as Redis)

## Relational Databases

In a relational database, data is organized into tables with rows and columns.
Each row represents a record, and each column represents a field in that record.
Tables in a relational database are related to each other through foreign keys, which are fields that reference the primary key of another table.

## NoSQL Databases
NoSQL databases are a type of database that do not follow the traditional relational model. They are designed to handle large amounts of unstructured data and to scale horizontally across multiple servers.

There are several different types of NoSQL databases, including:
* Document databases (such as MongoDB)
* Key-value stores (such as Redis)
* Column-family databases (such as Cassandra)
* Graph databases (such as Neo4j)

### In-Memory Databases

In-memory databases are databases that store all data in memory rather than on disk. They are very fast, but they are limited in the amount of data they can store by the amount of memory available on the server.

## SQL vs NoSQL vs In-Memory

When choosing which type of database to use, it is important to consider the specific requirements of the application.
* Relational databases (SQL) are well-suited for structured data and for applications that require strong consistency and transactions.
* NoSQL databases are better for unstructured data and for applications that require high scalability and availability.
* In-memory databases are best for applications that require extremely high performance, but they are limited in the amount of data they can store.

## ORMs
ORMs (Object-Relational Mappers) are tools that allow developers to work with a database using an object-oriented interface rather than writing raw SQL queries.
Ecto is an example of an ORM for Elixir.

## Indexes
Indexes are used to speed up the performance of database queries. They are essentially a way of creating a structured summary of the data in a table, which allows the database to quickly find the rows that match a given condition.

## Database Design
Proper database design is important for the performance and scalability of an application. This includes:
* Selecting the appropriate data types
* Choosing the right keys (primary and foreign)
* Creating the right indexes

It is important to consider the trade-offs between normalization (minimizing redundancy in the data) and denormalization (duplicating data to improve query performance) when designing a database schema.

## Transactions
Transactions allow multiple database operations to be executed as a single unit of work, either committing all the changes or rolling them back if an error occurs. This helps to ensure the integrity of the data in the database.
