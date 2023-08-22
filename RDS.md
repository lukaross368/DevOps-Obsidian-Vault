#cloud #AWS #devops #dataBases #awsServices 

### Introduction

Relational Database Service - A managed relational database (see [[Databases]]) service provided by AWS. Using this service will make it easier to set up, operate and scale relational databases in the AWS cloud. Some of its important features include; 

- Dashboard
- Databases
- Query 
- Editor
- Performance Insights
- Snapshots

Different Database engines that are supported by RDS are:

- MySQL
- SQL Server
- PostgreSQL
- Oracle
- MariaDB
- Amazon Aurora
- Amazon RDS Custom

### Why choose RDS over EC2 and On-premises

Why can we not just run our database in an AWS [[EC2]] Instance? Basically it depends on how much we as a customer of AWS want them to manage for us. Running our Database on premise means we manage everything (Server maintenance, Hardware lifecycle, Cooling, Networking, etc.) and similarly if we run our Database on an EC2 instance, while AWS manage some of these aforementioned Tasks, we will have to manage Scaling, Database software installation, DB software patching, High availability, OS patching and so on. If we as customers are willing to pay amazon to manage these things for our Relational DB instances then Amazon RDS is a useful service for us.

### RDS Concepts

#### DB instance class

A DB instance class determines the computation and memory capacity of the DB instance. 

#### DB Instance storage 

Amazon EBS provides durable, block level storage volumes that you can attach to a running instance. DB instance storage comes in the following types

- General Purpose (SSD)
- Provisioned IOPS (PIOPS)
- Magnetic
### Snapshots

With RDS you can schedule how often you want your database backed up with snapshots.