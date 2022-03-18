# 7280Project2
This is the project 2 of CS7280
## Introduction
[Apache Cassandra](https://cassandra.apache.org/_/index.html) 
  Cassandra is an open-source distributed NoSQL database system, which was originally developed by Facebook, aims to improve the search performance of email systems for simple format data, combining the data model of Google BigTable with the fully distributed architecture of Amazon Dynamo. The name Cassandra came from Greek mythology, the name of a tragic prophetess of Troy, so the logo of the project is a shining eye.
 
  In 2008 summer, Cassandra was discharged by Facebook on Google code as an open-sourced project. Then the project got to be an Apache Hatchery extend in Spring 2009. After graduation from Facebook, Cassandra become an official top-level project in ASP (Apache Software Foundation) on Feb 17, 2010.
## Installation process
1.	Firstly we went to the official website download link: https://cassandra.apache.org/_/quickstart.html
Follow the step instructions on getting started:
```
DOCKER PULL CASSANDRA:LATEST
```

2.	Then we start the Cassandra by running
```
docker run --name cassandra cassandra
```

3.	Lastly, we install the docker image to start the CQL shell:
```
docker exec -it cass_cluster cqlsh
```

## Sample code to create database objects
As we mentioned before in Data Model section, keyspace and tables are the central points. This part will list and discuss the statement which can create, update information and remove the data in keyspace and tables.
**Create Keyspace**
```
CREATE KEYSPACE IF NOT EXISTS project WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '1' };
describe project;
```
**Drop Keyspace**
```
DROP KEYSPACE project;
```
## Sample code to use (CRUD) the database
**Create a table**
```
CREATE TABLE IF NOT EXISTS project.student_holiday (
student_id text PRIMARY KEY,
holidays int,
holiday_time_add timestamp
);
describe project.student_holiday;
```
**Insert some data**
```
INSERT INTO project.student_holiday
(student_id, holidays, holiday_time_add)
VALUES ('12345', 1, toTimeStamp(now()));

INSERT INTO project.student_holiday
(student_id, holidays, holiday_time_add)
VALUES ('23456', 2, toTimeStamp(now()));

INSERT INTO project.student_holiday
(student_id, holidays, holiday_time_add)
VALUES ('34567', 3, toTimeStamp(now()));

SELECT * FROM project.student_holiday;
```
 
**Update Operation**
```
UPDATE project.student_holiday SET holidays=4
WHERE student_id ='12345';
```
**Read Data**
```
SELECT holidays, holiday_time_add FROM project.student_holiday;
```
**Delete data from table**
```
DELETE holidays FROM project.student_holiday WHERE student_id ='34567';
```
