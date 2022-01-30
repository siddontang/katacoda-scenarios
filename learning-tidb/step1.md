## Install TiUP

We can use [TiUP](https://github.com/pingcap/tiup) to deploy and manage TiDB cluster. 

We need to install TiUP at first with the following command:

```sh
curl --proto '=https' --tlsv1.2 -sSf https://tiup-mirrors.pingcap.com/install.sh | sh

source ~/.bashrc
```{{execute}}

## Use TiDB cloud

We can also a Develop Tier directly on [TiDB cloud](https://tidbcloud.com/) directly. 


## Start TiDB cluster

Start a TiDB cluster locally with following command:

`tiup playground --tag test --pd.host [[HOST_IP]] --tiflash 0 nightly`{{execute}}

## Use TiDB

TiDB is MySQL compatible, so we can use any MySQL client to connect to TiDB. 


Connect to TiDB

`mysql -h 127.0.0.1 -P 4000 -uroot`{{execute T2}}


If we use TiDB cloud, we can click the Connect button and get the access like like:
 
`mysql -u root -h tidb.5b486b69.1ef404eb.us-west-2.prod.aws.tidbcloud.com -P 4000 -p`{{copy}}

Create the northwind database

`source ~/northwind/northwind.sql;`{{execute T2}}

Prepare northwind data

`source ~/northwind/northwind-data.sql;`{{execute T2}}

Have a fun:

`select count(*) from customers;`{{execute T2}}