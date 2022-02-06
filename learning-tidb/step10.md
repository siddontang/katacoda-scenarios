In the previous examples, we all use one statement. Now, let's introduce Transaction.

As a distributed database, TiDB fully meets ACID requirement, supports both optimistic and pessimistic transaction and also supports multiple isolation modes. Refer to [Transactions](https://docs.pingcap.com/tidb/stable/transaction-overview)

Let's start with a simple example:

```sh
use northwind;
drop table if exists t;
create table t (id int primary key, name varchar (256));
```{{execute}}

Start a transaction with `begin`

```sh
begin;
insert into t values (1, "a");
commit;
```{{execute}}

If we don't commit the transaction, in another terminal, if we use `select * from t`{{copy}}, we can't see any result.

After the transaction is committed, we can see the data is inserted:

`select * from t;`{{execute}}

```bash
+----+------+
| id | name |
+----+------+
|  1 | a    |
+----+------+
```

We can roll back the transaction:

```sh
begin;
insert into t values (1, "a");
rollback;
```{{execute}}

After the transaction is rolled back, we can't see the data is inserted:

```bash
+----+------+
| id | name |
+----+------+
|  1 | a    |
+----+------+
```






