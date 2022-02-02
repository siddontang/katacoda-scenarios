In the previous sections, we all talk about how to retrieve data from TiDB, here we will show how to operate the date.

Let's create an example table at first:

```sh
drop table if exists t;
create table t(id int primary key, name varchar(256));
```{{execute}}

Insert some data:

`insert into t values (1, "a"), (2, "b"), (3, "c");`{{execute}}

`select * from t;`{{execute}}

```bash
+----+------+
| id | name |
+----+------+
|  1 | a    |
|  2 | b    |
|  3 | c    |
+----+------+
```

Then update the data:

`update t set name = 'cc' where id = 3;`{{execute}}

`select * from t where id = 3;`{{execute}}

Check the data has already been updated:
```bash
+----+------+
| id | name |
+----+------+
|  3 | cc   |
+----+------+
```

Insert the same data, we must meet an error:

`insert into t values (3, "c");`{{execute}}

The Error message is: `ERROR 1062 (23000): Duplicate entry '?' for key 'PRIMARY'`


We can delete the data and insert again:

`delete from t where id = 3;`{{execute}}

We can use `select * from t where id = 3;`{{execute}} to check that the data is not existed now.

Then insert again:

`insert into t values (3, "c");`{{execute}}

We can use `insert on duplicate key update` to insert the duplicated data:

`insert into t values (3, "c") on duplicate key update name = "cc";`{{execute}}

`select * from t where id = 3;`{{execute}}

```bash
+----+------+
| id | name |
+----+------+
|  3 | cc   |
+----+------+
```

We can update the data:

`update t set name = "c" where id = 3;`{{execute}}

`select * from t where id = 3;`{{execute}}

```bash
+----+------+
| id | name |
+----+------+
|  3 | c    |
+----+------+
```

