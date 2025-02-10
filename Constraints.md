# Constraints

## Null Values
In SQL, a cell with a NULL value indicates the value is missing. A NULL value is different from a zero value.

When creating a table, we can define if a field can or cant be NULL. Thats a kind of **constraint**.

## Constraints
A `contraint` is a rule we create on a db that enforces some specific behaviour. Ex, setting a `NOT NULL` constraint on a column ensures it wont accept `NULL` values.\
If we try to insert the NULL value, it will fail with an error message.
```
CREATE TABLE employees(
    id INTEGER PRIMARY KEY,
    name TEXT UNIQUE,
    -- The UNIQUE constraint ensures that no two rows can have the same value in the 'name' column
    title TEXT NOT NULL
    -- The NOT NULL constraint ensures that the 'title' column cannot have NULL values
);
```

## Primary Keys
A *key* defines and protects relationships between tables. A `primary key` is a special column that uniquely identifies records within a table. Each table can have one, and only one primary key.

### You Primary key will almost always be the "id" column

Its very common to have a column named `id` on each table in db, and its the primary key for that table. No two rows can share an id. 

## Foreign Keys
Foreign keys are what makes relational dbs relational! Foreign keys define the relationships between tables. A `FOREIGN KEY` is a field in one table that references another table's `PRIMARY KEY`. \
Creating a Foreign key in SQLite happens in table creation! After defining fields and constraints, we add a named constraint to define `FOREIGN KEY` column and its `REFERENCES` \
Example:  
```
CREATE TABLE departments (
    id INTEGER PRIMARY KEY,
    department_name TEXT NOT NULL
);

CREATE TABLE employees (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    department_id INTEGER,
    CONSTRAINT fk_departments
    FOREIGN KEY (department_id)
    REFERENCES departments(id)
);
```
In this example, an employee has a department_id. The department_id must be the same as the id field of a record from the departments table. fk_departments is the specified name of the constraint.

1. `CONSTRAINT fk_departments`: create a constraint called fk_departments

2. `FOREIGN KEY (department_id)`: make this constraint a foreign key assigned to the department_id field

3. `REFERENCES departments(id)`: link the foreign field id from the departments table

## Schema
 Schema describes how data is organized within the db. \
 Theres no perfect way to architect it. 

 ## Relational Database
 A *relational database* is a type of db that stores data so that it can be easily related to other data. A `user` can have many `tweets`. So relation between user and tweet.\
 In a relational db:
 1. Data is typically represented in “tables”.
 2. Each table has “columns” or “fields” that hold attributes related to the record.
 3. Each row or entry in the table is called a record.
 4. Typically, each record has a unique Id called the primary key.