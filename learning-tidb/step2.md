We can use [`select`](https://docs.pingcap.com/tidb/stable/sql-statement-select) command to query the data. 

## Select One Column

Let's start with a simple query:

`select first_name from employees;`{{execute T2}}

The above query will select data of the column named `first_name` from table `employees`, the result may like below:

```bash
+------------+
| first_name |
+------------+
| Andrew     |
| Anne       |
| Jan        |
| Laura      |
| Mariya     |
| Michael    |
| Nancy      |
| Robert     |
| Steven     |
+------------+
```

## Select Multi Columns

We can also retrieve multi columns' data:


`select first_name, last_name from employees;`{{execute T2}}

The result is:

```bash
+------------+----------------+
| first_name | last_name      |
+------------+----------------+
| Nancy      | Freehafer      |
| Andrew     | Cencini        |
| Jan        | Kotas          |
| Mariya     | Sergienko      |
| Steven     | Thorpe         |
| Michael    | Neipper        |
| Robert     | Zare           |
| Laura      | Giussani       |
| Anne       | Hellung-Larsen |
+------------+----------------+
```

## Select All Columns

We can also use `select * from employees;`{{execute T2}} to retrieve all the rows of the table.

## Select Distinct Rows

Sometimes, if we want to get the distinct rows, we can use the `distinct` keyword in the query, like:

`select distinct city from employees;`{{execute T2}}

## Select Limited Rows

If we want to only select limited rows, we can use the `limit` keyword like:

`select first_name from employees limit 2;`{{execute T2}}

The result is:

```bash
+------------+
| first_name |
+------------+
| Andrew     |
| Anne       |
+------------+
```

The above query gets two rows only, if we want to get the next three rows from the first two rows, we can use the `offset` keyword, like:

`select first_name from employees limit 3 offset 2;`{{execute T2}}

The result is

```bash
+------------+
| first_name |
+------------+
| Jan        |
| Laura      |
| Mariya     |
+------------+
```

We can also use `limit M,N` to simplify `limit N offset M`, so the above query can be changed to:

`select first_name from employees limit 2,3;`{{execute T2}}

Notice: don't get the `M,N` order confused, the first one is for the offset. 