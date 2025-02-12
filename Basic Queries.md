# Basic Queries

## As Clause in SQL
Sometimes we need to structure the data we return from our queries in a specific way. An `AS` clause allows us to alias a piece of data in our query. It only exists for the duration of the query. \
Both these return same data:
```
SELECT employee_id AS id, employee_name AS name
FROM employees;
```
```
SELECT employee_id, employee_name
FROM employees;
```
Difference is that aliased query will have column names id and name instead of employee_id and employee_name.

## SQL Functions
We can use functions and aliases to calculate new columns in a query. Similar to how you might use formulas in Excel.
### IIF Function
Works as a turnery. 
```
IIF(carA > carB, 'Car a is bigger', 'Car b is bigger')
```
If a is greater than b, this statement evaluates to the string `Car a is bigger`, otherwise `Car b is bigger`
Heres how to use it and a directive alias to add new calculated column to result set:
```
SELECT quantity,
    IIF(quantity < 10, 'Order more', 'In Stock') AS directive
    FROM products;
```

### Between
We can check if two values are between two numbers using `WHERE`, we can use it to narrow down the result set.
```
SELECT employee_name, salary
FROM employees
WHERE salary BETWEEN 30000 and 60000;
```
Returns all employees name and salary fields for any rows where salary is between 30k to 60k, can also use `NOT BETWEEN`

### Distinct
This will remove duplicate records from the resulting query.
```
SELECT DISTINCT previous_company
    FROM employees;
```
This only returns one row for each unique previous_company value.

### Logical operators - AND
Can use it to narrow down our result sets even more!
```
SELECT product_name, quantity, shipment_status
    FROM products
    WHERE shipment_status = 'pending'
    AND quantity BETWEEN 0 and 10;
```
This only retrieves records where both the shipment_status is “pending” AND the quantity is between 0 and 10.

### Logical operators - OR
or is also supported!
```
SELECT product_name, quantity, shipment_status
    FROM products
    WHERE shipment_status = 'out of stock'
    OR quantity BETWEEN 10 and 100;
```
This query retrieves records where either the shipment_status condition OR the quantity condition are met.

### Order of operations
You can group logical operations with parentheses to specify the order of operations.
```
(this AND that) OR the_other
```

### In
IN returns true or false if first operand matches any of the values in second operand.
```
SELECT product_name, shipment_status
    FROM products
    WHERE shipment_status IN ('shipped', 'preparing', 'out of stock');
```
same as 
```
SELECT product_name, shipment_status
    FROM products
    WHERE shipment_status = 'shipped'
        OR shipment_status = 'preparing'
        OR shipment_status = 'out of stock';
```

### Like
The LIKE keyword allows for the use of the % and _ wildcard operators. Allows us to query something we know a part of.

**% operator** \
The % operator will match zero or more characters. We can use this operator within our query string to find more than just exact matches depending on where we place it. \
- Starts with "banana" : WHERE product_name LIKE 'banana%';
- Ends with "banana" : WHERE product_name LIKE '%banana';
- Contains "banana" : WHERE product_name LIKE '%banana%';

**_ operator** \
 the _ wildcard operator only matches a single character. Each _ is a single char.
 - WHERE product_name LIKE '__oot'; \
 This will be something like shoot or groot.


### All Equality operators
- `=`
- `<`
- `>`
- `<=`
- `>=`