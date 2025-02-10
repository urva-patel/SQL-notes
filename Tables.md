# Tables 

## Creating a Table

Use the **CREATE TABLE** statement followed by the name of the table and the fields you want in the table(can use whitespace as well after commas)\
`CREATE TABLE employees (id INTEGER, name TEXT, age INTEGER, is_manager BOOLEAN, salary INTEGER);` 

## Altering Tables
We can alter table with **ALTER TABLE** instead of delete and recreate. Allows you to:
### Rename a table or column
```
ALTER TABLE employees
RENAME TO contractors;

ALTER TABLE contractors
RENAME COLUMN salary TO invoice; 
```

### Add or DROP a Column
```
ALTER TABLE contractors
ADD COLUMN job_title TEXT;

ALTER TABLE contractors
DROP COLUMN is_manager;
```


## Intro to Migration
A db *migration* is a set of changes to a relational db. The **ALTER TABLE** statement is example of migration!
Good migrations are small incremental and ideally reversable changes to a db.

### Example of bad migration
If we need something like `SELECT * FROM people` and then we have a db migration that alters table name from `people` to `users` *without updating the code*, the application will break!\
Simple solution is to deploy new code that uses new query:\
`SELECT * FROM users`\
and deploy that code to prod immediately after the migration.

### Migration Practice

When writing reversable migrations, we use terms "up" and "down" migrations. "up" migration is the set of changes you want to make, like alter/add/remove table. "down" migration includes changes that would revert any of the "up" changes".