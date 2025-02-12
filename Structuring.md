# Structuring

When using both ORDER BY and LIMIT, the ORDER BY clause must come first.
## Limit
The `LIMIT` keyword can be used at the end of a select statement to reduct the num of records returned.
```
SELECT * FROM products
    WHERE product_name LIKE '%berry%'
    LIMIT 50;
```
The LIMIT statement only allows the database to return up to 50 records matching the query. 

## Order By
By default, the `ORDER BY` keyword sorts records by the given field in ascending order, or `ASC` for short. However, ORDER BY does support descending order as well with the keyword `DESC`.
ASC:
```
SELECT name, price, quantity FROM products
    ORDER BY price;
```
DESC:
```
SELECT name, price, quantity FROM products
    ORDER BY quantity DESC;
```