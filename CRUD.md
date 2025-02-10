# CRUD

CRUD is an acronym that stands for CREATE, READ, UPDATE and DELETE. The 4 operations are bread and butter of each db we create.

## HTTP and CRUD
The CRUD operations correlate nicely with the HTTP methods we learned in the Learn HTTP Clients course.

- HTTP POST - CREATE
- HTTP GET - READ
- HTTP PUT - UPDATE
- HTTP DELETE - DELETE

## Insert Statement
We can add records to a table using an `INSERT INTO` statement. When using an `INSERT` statement we must specift the table we are inserting into, then the fields within that table we want to add VALUES to.\
Example `INSERT INTO` statement:
```
INSERT INTO employees(id, name, title)
VALUES (1, 'Allan', 'Engineer');
```

## Auto Increment
Many dialects of SQL support `AUTO INCREMENT`. When inserting records into a table with it enabled, the db assigns the next value automatically. In SQLite, an int id field that has PRIMARY KEY constraint will auto increment default! Not uuid though, your server needs to handle that. \
So if the column has `INTEGER PRIMARY KEY` it auto increments.

## Manual Entry
Manually inserting each record would take too long. When working with SQL in a software system, your language like go or python can do it. Like with Go, you can do something like 
```
sqlQuery := fmt.Sprintf(`
INSERT INTO users(name, age, country_code)
VALUES ('%s', %v, '%s');
`, user.Name, user.Age, user.CountryCode)
```

## Count
We can use `SELECT` to get a count of records within a table, this is useful when we need to know how many records there are. \
`SELECT COUNT(*) FROM employees;`\
The * refers to a column name. Can use wildcard * since we want to know number of total records, dont care about specific column

## WHERE Clause
In order to keep learning about CRUD in SQL, need to know how to make the instructions to a db more specific. `WHERE` statement within a query allows us to be specific.
### Using a WHERE Clause
If we had 9000 records, we want to look at specific data without getting all other records. We can use `SELECT` followed by `WHERE` clause to specifty which records to retrieve. 
```
SELECT name FROM users WHERE power_level >= 9000;
```
This selects only the `name` field in `users` table `WHERE` the `power_level` is greater or equal to 9000.
### Finding NULL with WHERE
Can use WHERE to filter values by whether or not theyre NULL.
```
SELECT name FROM users WHERE first_name IS NOT NULL;
```
### Deleting with WHERE
a `DELETE` statement removes all records from a table that match the `WHERE` clause.
```
DELETE FROM employees
    WHERE id = 251;
```

**Strategy when deleting data**\
Data can be hard/impossible to restore. Heres some strategies:\
**Backups**: Turn on automated backups, it takes a automated screenshot of your db on an interval.\
**Soft Deletes**: This is where you dont actually delete the data, you just mark it deleted. You set a deleted_at date on the row, then in teh queries you ignore it. Automated backups are usually good enough rather than this.