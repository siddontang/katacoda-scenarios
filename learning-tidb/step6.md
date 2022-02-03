Refer to [Function and Operator Reference](https://docs.pingcap.com/tidb/stable/functions-and-operators-overview), we can see that TiDB has supported many functions, here we just introduce some.

## String functions

Get the full name of the employee:

`select concat(last_name, " ", first_name) as fullname from employees;`{{execute}}

```bash
+---------------------+
| fullname            |
+---------------------+
| Freehafer Nancy     |
| Cencini Andrew      |
| Kotas Jan           |
| Sergienko Mariya    |
| Thorpe Steven       |
| Neipper Michael     |
| Zare Robert         |
| Giussani Laura      |
| Hellung-Larsen Anne |
+---------------------+
```

Get the lower or upper first name

`select lower(first_name) from employees;`{{execute}}

```bash
+-------------------+
| lower(first_name) |
+-------------------+
| andrew            |
| anne              |
| jan               |
| laura             |
| mariya            |
| michael           |
| nancy             |
| robert            |
| steven            |
+-------------------+
```


## Date and Time functions

Get current date and time:

`select now();`{{execute}}

Notice: we may see a different result when execute the above query.
```bash
+---------------------+
| now()               |
+---------------------+
| 2022-02-03 04:27:12 |
+---------------------+
```

Get the unix timestamp:

`select unix_timestamp();`{{execute}}

`select extract(year from "2022-01-01") as year;`{{execute}}

```bash
+------+
| year |
+------+
| 2022 |
+------+
```

## Numeric functions

Get PI:

`select pi();`{{execute}}

```bash
+----------+
| pi()     |
+----------+
| 3.141593 |
+----------+
```

Get the absolute value:

`select abs(-1);`{{execute}}

```bash
+---------+
| abs(-1) |
+---------+
|       1 |
+---------+
```


