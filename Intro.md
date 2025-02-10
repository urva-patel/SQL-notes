# Intro to SQL

## SQL databases
Theres many to pick from! 
- SQLite
- PostgreSQL
- MySQL
- CockroachDB
- Oracle
- etc…

### SQLite specific notes
It stores Boolean values as integers, 0 and 1

SQLite is a serverless db management system(DBMS) that has ability to run within applications, whereas PostgreSQL uses client-server model and requires a server to be installed and listening on a network, like HTTP server

**SQLite Data Types**
1. NULL - Null value.
2. INTEGER - A signed integer stored in 0,1,2,3,4,6, or 8 bytes.
3. REAL - Floating point value stored as an 64-bit IEEE floating point number.
4. TEXT - Text string stored using database encoding such as UTF-8
5. BLOB - Short for Binary large object and typically used for images, audio or other multimedia.
6. BOOLEAN - Boolean values are written in SQLite queries as true or false, but are recorded as 1 or 0.

## SQL vs NoSQL
Differences:
- NoSQL are non relational, SQL are relational.
- SQL have a defined schema, NoSQL have a dynamic schema
- SQL are table-based, NoSQL db have variety of storage methods (document, key-value, graph, wide-column and more)

## SELECT

**SELECT** is the most common operation in SQL, its called a *query*.\
Standard **SELECT** do not alter the DB.

Here are a couple examples for single, multiple and all in order:\
`SELECT id FROM users;`\
`SELECT id, name FROM users;`\
`SELECT * FROM users;`




