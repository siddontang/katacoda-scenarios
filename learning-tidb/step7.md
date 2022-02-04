How can we know that who buys the product "Northwind Traders Chai" in the northwind database?

We may do the following steps:

1. Get the product ID with the product name in the `products` table.

`select id from products where product_name = "Northwind Traders Chai";`{{execute}}
```bash
+----+
| id |
+----+
|  1 |
+----+
```

2. Get the order ID with the product ID in the `order_details` table.

`select order_id from order_details where product_id = 1;`{{execute}}

```bash
+----------+
| order_id |
+----------+
|       32 |
|       44 |
+----------+
```

3. Get the customer ID with the order ID in the `orders` table.

`select customer_id from orders where id in (32, 44);`{{execute}}

```bash
+-------------+
| customer_id |
+-------------+
|          12 |
|           1 |
+-------------+
```

4. Get the customer name with the customer ID in the `customers` table.

`select concat(last_name, " ", first_name) as name from customers where id in (1, 12);`{{execute}}

```bash
+--------------+
| name         |
+--------------+
| Bedecs Anna  |
| Edwards John |
+--------------+
```

We can combine the above steps together using subquery:

`select concat(last_name, " ", first_name) as name from customers where id in (select customer_id from orders where id in ( select order_id from order_details where product_id in (select id from products where product_name = "Northwind Traders Chai")));`{{execute}}

```bash
+--------------+
| name         |
+--------------+
| Bedecs Anna  |
| Edwards John |
+--------------+
```

How can we know the number of orders the people placed? We can:

1. Get the customer ID 
2. Get the count for each customer from `orders`
3. Combine all the rows together


Here, we can use `subquery` as operand instead:

`select concat(first_name, " ", last_name) as name, (select count(*) from orders where orders.customer_id = customers.id) as orders from customers order by orders desc;`{{execute}}

```bash
+--------------------------+--------+
| name                     | orders |
+--------------------------+--------+
| Elizabeth Andersen       |      6 |
| Francisco Pérez-Olaeta   |      6 |
| Christina Lee            |      5 |
| Amritansh Raghav         |      4 |
| Roland Wacker            |      4 |
| Soo Jung Lee             |      4 |
| Thomas Axen              |      3 |
| Anna Bedecs              |      2 |
| Peter Krschne            |      2 |
| Karen Toh                |      2 |
| John Rodman              |      2 |
| Ming-Yang Xie            |      2 |
| Sven Mortensen           |      2 |
| John Edwards             |      2 |
| Run Liu                  |      2 |
| Antonio Gratacos Solsona |      0 |
| Martin O’Donnell         |      0 |
| Andre Ludick             |      0 |
| Carlos Grilo             |      0 |
| Helena Kupkova           |      0 |
| Daniel Goldschmidt       |      0 |
| Jean Philippe Bagel      |      0 |
| Catherine Autier Miconi  |      0 |
| Alexander Eggerer        |      0 |
| George Li                |      0 |
| Bernard Tham             |      0 |
| Luciana Ramos            |      0 |
| Michael Entin            |      0 |
| Jonas Hasselberg         |      0 |
+--------------------------+--------+
```

