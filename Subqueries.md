# Subqueries

## Subquery 
It is possible to run a query on the result set of another query - a query within a query! This is a `subquery`\
Getting data from multiple tables:
```
SELECT id, song_name, artist_id
FROM songs
WHERE artist_id IN (
    SELECT id
    FROM artists
    WHERE artist_name LIKE 'Rick%'
);
```
In this hypothetical database, the query above selects all of the ids, song_names, and artist_ids from the songs table that are written by artists whose name starts with “Rick”. Notice that the subquery allows us to use information from a different table - in this case the artists table.

## No tables
You can `SELECT` information that is calculated with no tables necessary
```
SELECT 5 + 10 as sum;
```