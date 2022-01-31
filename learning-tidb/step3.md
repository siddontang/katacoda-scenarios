## Sort rows with order

Sometimes, when we retrieve some rows, we find that the result rows are not ordered.

`select email_address from employees;`{{execute T2}}

```bash
+------------------------------+
| email_address                |
+------------------------------+
| nancy@northwindtraders.com   |
| andrew@northwindtraders.com  |
| jan@northwindtraders.com     |
| mariya@northwindtraders.com  |
| steven@northwindtraders.com  |
| michael@northwindtraders.com |
| robert@northwindtraders.com  |
| laura@northwindtraders.com   |
| anne@northwindtraders.com    |
+------------------------------+
```

If we want to get a ordered result, we can use `order by` clause, like:


`select email_address from employees order by email_address;`{{execute T2}}

```bash
+------------------------------+
| email_address                |
+------------------------------+
| andrew@northwindtraders.com  |
| anne@northwindtraders.com    |
| jan@northwindtraders.com     |
| laura@northwindtraders.com   |
| mariya@northwindtraders.com  |
| michael@northwindtraders.com |
| nancy@northwindtraders.com   |
| robert@northwindtraders.com  |
| steven@northwindtraders.com  |
+------------------------------+
```


## Sort rows with multi columns by order

We can use `order by` to sort multi columns, e.g. 

`select first_name, last_name, job_title from employees;`{{execute T2}}

```bash
+------------+----------------+-----------------------+
| first_name | last_name      | job_title             |
+------------+----------------+-----------------------+
| Nancy      | Freehafer      | Sales Representative  |
| Andrew     | Cencini        | Vice President, Sales |
| Jan        | Kotas          | Sales Representative  |
| Mariya     | Sergienko      | Sales Representative  |
| Steven     | Thorpe         | Sales Manager         |
| Michael    | Neipper        | Sales Representative  |
| Robert     | Zare           | Sales Representative  |
| Laura      | Giussani       | Sales Coordinator     |
| Anne       | Hellung-Larsen | Sales Representative  |
+------------+----------------+-----------------------+
```

If we want to sort by `job_title` at first, then by `first_name`, we can use below:

`select job_title, first_name, last_name from employees order by job_title, first_name;`{{execute T2}}

```bash
+-----------------------+------------+----------------+
| job_title             | first_name | last_name      |
+-----------------------+------------+----------------+
| Sales Coordinator     | Laura      | Giussani       |
| Sales Manager         | Steven     | Thorpe         |
| Sales Representative  | Anne       | Hellung-Larsen |
| Sales Representative  | Jan        | Kotas          |
| Sales Representative  | Mariya     | Sergienko      |
| Sales Representative  | Michael    | Neipper        |
| Sales Representative  | Nancy      | Freehafer      |
| Sales Representative  | Robert     | Zare           |
| Vice President, Sales | Andrew     | Cencini        |
+-----------------------+------------+----------------+
```


## Sort rows with specified direction

The default order direction is ascending, we can use `desc` to descending sort:

`select job_title, first_name, last_name from employees order by job_title, first_name desc;`{{execute T2}}

```bash
+-----------------------+------------+----------------+
| job_title             | first_name | last_name      |
+-----------------------+------------+----------------+
| Sales Coordinator     | Laura      | Giussani       |
| Sales Manager         | Steven     | Thorpe         |
| Sales Representative  | Robert     | Zare           |
| Sales Representative  | Nancy      | Freehafer      |
| Sales Representative  | Michael    | Neipper        |
| Sales Representative  | Mariya     | Sergienko      |
| Sales Representative  | Jan        | Kotas          |
| Sales Representative  | Anne       | Hellung-Larsen |
| Vice President, Sales | Andrew     | Cencini        |
+-----------------------+------------+----------------+
```

As we can see, in the above result, `Robert` is the first one with the same job title "Sales Representative" now. 

We can add `desc` to any column, e.g.

`select job_title, first_name, last_name from employees order by job_title desc, first_name;`{{execute T2}}

```bash
+-----------------------+------------+----------------+
| job_title             | first_name | last_name      |
+-----------------------+------------+----------------+
| Vice President, Sales | Andrew     | Cencini        |
| Sales Representative  | Anne       | Hellung-Larsen |
| Sales Representative  | Jan        | Kotas          |
| Sales Representative  | Mariya     | Sergienko      |
| Sales Representative  | Michael    | Neipper        |
| Sales Representative  | Nancy      | Freehafer      |
| Sales Representative  | Robert     | Zare           |
| Sales Manager         | Steven     | Thorpe         |
| Sales Coordinator     | Laura      | Giussani       |
+-----------------------+------------+----------------+
```

Or to all columns in the order by clause:

`select job_title, first_name, last_name from employees order by job_title desc, first_name desc;`{{execute T2}}

```bash
+-----------------------+------------+----------------+
| job_title             | first_name | last_name      |
+-----------------------+------------+----------------+
| Vice President, Sales | Andrew     | Cencini        |
| Sales Representative  | Robert     | Zare           |
| Sales Representative  | Nancy      | Freehafer      |
| Sales Representative  | Michael    | Neipper        |
| Sales Representative  | Mariya     | Sergienko      |
| Sales Representative  | Jan        | Kotas          |
| Sales Representative  | Anne       | Hellung-Larsen |
| Sales Manager         | Steven     | Thorpe         |
| Sales Coordinator     | Laura      | Giussani       |
+-----------------------+------------+----------------+
```