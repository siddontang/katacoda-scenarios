## Use `where`

Mostly, we want to get our data by some conditions, here we can use `where`, like below:

`select first_name, last_name, job_title from employees where first_name = "Anne";`{{execute}}

```bash
+------------+----------------+----------------------+
| first_name | last_name      | job_title            |
+------------+----------------+----------------------+
| Anne       | Hellung-Larsen | Sales Representative |
+------------+----------------+----------------------+
```

## Operator in `where`

In the above example we use `=` operator which means equal here, we can use others in the `where` clause. 

Not equal: `!=` or `<>`


`select first_name, last_name, job_title from employees where first_name != "Anne";`{{execute}}

```bash
+------------+-----------+-----------------------+
| first_name | last_name | job_title             |
+------------+-----------+-----------------------+
| Nancy      | Freehafer | Sales Representative  |
| Andrew     | Cencini   | Vice President, Sales |
| Jan        | Kotas     | Sales Representative  |
| Mariya     | Sergienko | Sales Representative  |
| Steven     | Thorpe    | Sales Manager         |
| Michael    | Neipper   | Sales Representative  |
| Robert     | Zare      | Sales Representative  |
| Laura      | Giussani  | Sales Coordinator     |
+------------+-----------+-----------------------+
```

Less: '<'
Less or equal: `<=`
Greater '>', 
Greater or equal: `>=`

`select first_name, last_name, job_title from employees where first_name <= "Anne";`{{execute}}

```bash
+------------+----------------+-----------------------+
| first_name | last_name      | job_title             |
+------------+----------------+-----------------------+
| Andrew     | Cencini        | Vice President, Sales |
| Anne       | Hellung-Larsen | Sales Representative  |
+------------+----------------+-----------------------+
```

Between in two values: `between and`

`select first_name, last_name, job_title from employees where first_name between "A" and "B";`{{execute}}

```bash
+------------+----------------+-----------------------+
| first_name | last_name      | job_title             |
+------------+----------------+-----------------------+
| Andrew     | Cencini        | Vice President, Sales |
| Anne       | Hellung-Larsen | Sales Representative  |
+------------+----------------+-----------------------+
```


## Advanced Operator in `where`

We can combine multi conditions in the `where` clause, like:

AND: each condition must be True 

`select first_name, last_name, job_title from employees where job_title = "Sales Representative" and first_name = "Jan";`{{execute}}

```bash
+------------+-----------+----------------------+
| first_name | last_name | job_title            |
+------------+-----------+----------------------+
| Jan        | Kotas     | Sales Representative |
+------------+-----------+----------------------+
```

`select first_name, last_name, job_title from employees where job_title = "Sales Representative" and first_name = "Jane";`{{execute}}

"Jane" is not existed in the table, so the result is empty.


OR: if any condition is True, then True

`select first_name, last_name, job_title from employees where job_title = "Sales Representative" or first_name = "Jane";`{{execute}}

```bash
+------------+----------------+----------------------+
| first_name | last_name      | job_title            |
+------------+----------------+----------------------+
| Nancy      | Freehafer      | Sales Representative |
| Jan        | Kotas          | Sales Representative |
| Mariya     | Sergienko      | Sales Representative |
| Michael    | Neipper        | Sales Representative |
| Robert     | Zare           | Sales Representative |
| Anne       | Hellung-Larsen | Sales Representative |
+------------+----------------+----------------------+
```

IN:

`select first_name, last_name, job_title from employees where first_name in ("Jan", "Anne", "Jane");`{{execute}}

We know "Jan" and "Anne" are existed, but "Jane" isn't, so the query will return two rows.

```bash
+------------+----------------+----------------------+
| first_name | last_name      | job_title            |
+------------+----------------+----------------------+
| Jan        | Kotas          | Sales Representative |
| Anne       | Hellung-Larsen | Sales Representative |
+------------+----------------+----------------------+
```

## Wildcard 

Sometimes, if we don't know the exact value to filter, we can use a wildcard with `like`:

`select first_name, last_name, job_title from employees where first_name like "Ann%";`{{execute}}

```bash
+------------+----------------+----------------------+
| first_name | last_name      | job_title            |
+------------+----------------+----------------------+
| Anne       | Hellung-Larsen | Sales Representative |
+------------+----------------+----------------------+
```




