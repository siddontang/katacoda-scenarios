## Aggregation functions

Sometimes, we need to retrieve some aggregated result, maybe the most common use is to know how many rows in the table, here, we can use `count` like:

`select count(*) from products;`{{execute}}

```bash
+----------+
| count(*) |
+----------+
|       45 |
+----------+
```

Not only `count`, we can also use other aggregation functions, like `max`, `min`, `sum`, `avg`:

`select max(list_price) as max_price from products;`{{execute}}

```bash
+-----------+
| max_price |
+-----------+
|   81.0000 |
+-----------+
```

We can also combine these aggregation functions together:

`select count(list_price) as count, max(list_price) as max_price, min(list_price) as min_price from products;`{{execute}}

```bash
+-------+-----------+-----------+
| count | max_price | min_price |
+-------+-----------+-----------+
|    45 |   81.0000 |    1.2000 |
+-------+-----------+-----------+
```

## Group the data

In the above examples, we aggregate the rows for the whole table, we can also group the data, then do the aggregation.

Here we will use `group by` clause:

`select target_level, count(list_price) as count, max(list_price) as max_price, min(list_price) as min_price from products group by target_level;`{{execute}}

```bash
+--------------+-------+-----------+-----------+
| target_level | count | max_price | min_price |
+--------------+-------+-----------+-----------+
|           50 |     3 |    4.0000 |    2.0000 |
|           75 |     1 |    3.5000 |    3.5000 |
|           80 |     2 |   19.5000 |   17.0000 |
|          100 |     6 |   46.0000 |    4.0000 |
|           20 |     5 |   15.9900 |    9.2000 |
|          125 |     1 |    2.9900 |    2.9900 |
|          120 |     2 |   38.0000 |   18.4000 |
|          200 |     4 |    5.0000 |    1.8000 |
|           40 |    19 |   81.0000 |    1.2000 |
|           60 |     2 |   14.0000 |   13.0000 |
+--------------+-------+-----------+-----------+
```

We can use `group by` and `order by` together:

`select target_level, count(list_price) as count, max(list_price) as max_price, min(list_price) as min_price from products group by target_level order by target_level;`{{execute}}

```bash
+--------------+-------+-----------+-----------+
| target_level | count | max_price | min_price |
+--------------+-------+-----------+-----------+
|           20 |     5 |   15.9900 |    9.2000 |
|           40 |    19 |   81.0000 |    1.2000 |
|           50 |     3 |    4.0000 |    2.0000 |
|           60 |     2 |   14.0000 |   13.0000 |
|           75 |     1 |    3.5000 |    3.5000 |
|           80 |     2 |   19.5000 |   17.0000 |
|          100 |     6 |   46.0000 |    4.0000 |
|          120 |     2 |   38.0000 |   18.4000 |
|          125 |     1 |    2.9900 |    2.9900 |
|          200 |     4 |    5.0000 |    1.8000 |
+--------------+-------+-----------+-----------+
```


## Group and filter the data

We have already known that we can use condition to filter the data in the `where` clause, but `where` can only filter row, not group. If we want to filter the grouped data, we should use `having`:

`select target_level, count(list_price) as count, max(list_price) as max_price, min(list_price) as min_price from products group by target_level having target_level > 60;`{{execute}}

```bash
+--------------+-------+-----------+-----------+
| target_level | count | max_price | min_price |
+--------------+-------+-----------+-----------+
|          100 |     6 |   46.0000 |    4.0000 |
|           80 |     2 |   19.5000 |   17.0000 |
|          125 |     1 |    2.9900 |    2.9900 |
|          120 |     2 |   38.0000 |   18.4000 |
|          200 |     4 |    5.0000 |    1.8000 |
|           75 |     1 |    3.5000 |    3.5000 |
+--------------+-------+-----------+-----------+
```

Notice: we can't use `where` with `group by`.