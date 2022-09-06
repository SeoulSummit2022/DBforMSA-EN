# Tech Summit 2022 - DBforMSA Workshop

---

**Tech Summit 2022 - Welcome to DBfor MSA Workshop**

**You are going to split and to migrate from enterprise monolith Oracle to purpose built dababases**

---

#### Workshop Category

```
workshop00 - Creating KeyPair and Workshop Environment

workshop01 - Separation of CRM Report Service Using MongoDB

workshop02 - Real time leaderboard with Redis

workshop03 - Accelerate Limited Offer using REDIS

workshop04 - Migrating an order service using DynamoDB


```

---

#### Notes

```
% AWS launches new console UI for customer convenience, UI of workshop guides might be different from AWS console UI.

% In this workshop, we are using same server for Oracle, MongoDB and REDIS to reduce cost.
% You can use standalone for DEV/Test env, but it's better to use Amazon Managed Services
% to secure HA, Security, auto backup and operational excellence in Production env.

% You have to proceed workshop in Seoul Region(ap-northeast-2).

```

![image-20220501144253304](images/image-20220501144253304.png)



---

### Workshop Introduction

```
This workshop makes you understand how four services (CRM Report, Game Ranking, Limited Offer,
Order History) working in Oracle Monolith DB are migrated to REDIS, MongoDB, DynamoDB 
upon its respective purpose and the advantages of using DB properly upon purpose.

There are various ways like Custom Application, 3rd party solutions(sql developer, CDC, ETL tool), 
DB Engine native Utillity (datapump / dump) for Database to be migrated to the same or different  
DB engines. This workshop provides the practical exercise of utilizing 
AWS Database Migration Service with a few ways above. 

Each scenario and hands-on contents are like below and it represents the advantages to utilize
purpose-built databases by each scenario.

S1 – DB overload by Join Operation increases in case of workload that JOINs multiple tables 
to make one document as CRM report or articles in RDBMS. 
Especially, increasing the number of tables to JOIN makes the total overhead worse, 
which results in that the performance of total service decreases. 
The one of the best way to store and make the format of one document is to use 
Document type DB as a format of JSON. 
The performance of storing and making inquiries is improved when processing by one Document 
instead of JOINing multiple tables in existing RDBMS.

S2 – Game Ranking Service to REDIS
The process to sort all data by using the function rank() is required to make leader board (ranking) 
data in relational database. 
But due to many resources to be used for reading and sorting all data, it is hard to process 
directly within production database so it is better to configure the separate batch system 
to make data in the separate system and copy the resulted rank data to production database.
Customers can decrease the cost of system maintenance and be provided with faster and 
the real-time rank data when utilizing Redis sorted set 
which is appropriate for the data like leader board. 

S3- Hot Block can happen in case of the service that many users request/access at the same time 
like item limited-offer events. Hot Block brings about Latch contention or Lock contention inside DB, 
which results in the delay of event processing. Hot Block issue like this can happen in various workloads 
like billing system, event system, retail system and so on. 
This workshop shows how REDIS improves the performance against Hot Block generating in Oracle. 
In reality, AB test result will show you 4 times better performance when using REDIS rather than Oracle.  

S4- Order History Data to DynamoDB
As the number of users and requests on relational database increases, the performance becomes worse 
due to the impact of the relationship between tables, constraints, Join and etc 
and also scalability is limited for performance acceptance. 
NoSQL database like DynamoDB can be an alternative for this case. 
DynamoDB has almost limitless scalability and provides the consistent response speed when it scales.
Hands-on session will deliver how to migrate from relational database to DynamoDB and 
the test will show the response time at single-digit millisecond that DynamoDB provides. 

```



```
%Notice% This workshop is intended to understand the advantages of using databases for various purpose, rather than focusing on AWS Services. Therefore, various DBs are running on one EC2. You can use managed database services in AWS to secure HA/DR, Security, Backup & Recovery and Scale.
```



---



[Let's start workshop - workshop00(Creating workshop environment) ](./workshop00/workshop00.md) 

