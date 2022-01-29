## Install TiUP

You can use [TiUP](https://github.com/pingcap/tiup) to deploy and manage TiDB cluster. 

You need to install TiUP at first with the following command:

```sh
curl --proto '=https' --tlsv1.2 -sSf https://tiup-mirrors.pingcap.com/install.sh | sh

source ~/.bashrc
```{{execute}}



## Start TiDB cluster

You can start a TiDB cluster locally with following command:

`tiup playground --tag test --pd.host [[HOST_IP]] --tiflash 0 nightly`{{execute}}

## Use TiDB

TiDB is MySQL compatible, so you can use any MySQL client to connect to TiDB. 


Connect to TiDB

`mysql -h 127.0.0.1 -P 4000 -uroot`{{execute T2}}


Create the northwind database

`source ~/northwind/northwind.sql;`{{execute T2}}

Prepare northwind data

`source ~/northwind/northwind-data.sql;`{{execute T2}}

Have a fun:

`select count(*) from customers;`{{execute T2}}