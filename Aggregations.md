# Aggregations
An “aggregation” is a single value that’s derived by combining several other values. We performed an aggregation earlier when we used the COUNT statement to count the number of records in a table. \
When we need to calculate some additional data from the raw data, we can use an aggregation.
```
SELECT COUNT(*)
FROM products
WHERE quantity = 0;
```
This query returns the number of products that have a quantity of 0

## SUM
The `SUM` aggregation function returns the sum of a set of values.
For example, the query below returns a single record containing a single field. The returned value is equal to the total salary being collected by all of the employees in the employees table.
```
SELECT SUM(salary)
FROM employees;
```

## max 
The `max` function returns the largest value from a set of values:
```
SELECT max(price)
FROM products;
```
This query looks through all of the prices in the products table and returns the price with the largest price value.

## min
The `min` function works the same as the max function but finds the lowest value instead of the highest value.
```
SELECT product_name, min(price)
FROM products;
```
This query returns the product_name and the price fields of the record with the lowest price.

## GROUP BY
SQL offers the GROUP BY clause which can group rows that have similar values into “summary” rows. It returns one row for each group. \
The interesting part is that each group can have an aggregate function applied to it that operates only on the grouped data.
```
SELECT album_id, count(song_id)
FROM songs
GROUP BY album_id;
```
This query retrieves a count of all the songs on each album. One record is returned per album, and they each have their own count.

## Average
SQL offers us the `AVG()` function. Similar to MAX(), AVG() calculates the average of all non-NULL values.
```
SELECT avg(song_length)
FROM songs;
```
This query returns the average song_length in the songs table!

## Having
When need to filter results of `GROUP BY` futher, can use `HAVING`. It specifies a seach condition for a group. Similar to WHERE, but operates on groups after theyve been grouped. 
```
SELECT album_id, count(id) as count
FROM songs
GROUP BY album_id
HAVING count > 5;
```
This query returns the album_id and count of its songs, but only for albums with more than 5 songs.

## Round
`round()` allows you to specify both the value you wish to round and the precision to round it.
If no precision given, it will round to nearest whole value
```
round(value, precision)
```
