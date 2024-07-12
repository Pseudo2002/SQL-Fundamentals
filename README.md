# SQL-Fundamentals

1. SQL means structured query language
2. SQL is a common query language for accessing data in any relational database
3. Relational database means the database where data is stored in tabular format means in form of rows and columns.
4. A table represents an entity e.g. employee,student etc. The attributes of the entity are columns of the table.
The data for each instance of entity is the row.

e.g.
## EMPLOYEE:
eid	ename		salary	   cname
1	'nilesh'	45000	   'Infosys"
2	'mohan'		55000	   'wipro'
3	'mukesh'	58000	    'abc'

5. SQL consists of queries using which we can retrieve data from tables in database, insert data,update data etc.
7. The system which includes database and queries to obtain and process data from database are called relational database management system
8. SQL is declarative language. Here focus is on the output of the task and not how task is internally implemented. In sql the queries will provide command to the database to perform operation but how operation/query is internally implemented is hidden from user.
9. SQL is case insensitive. Here the case of commands upper or lower case doesn't matter
10. SQL is much easier to learn because it involves uses of English keywords. It involves less coding
11. SQL is used in client server systems in web applications or websites.
12. SQL can also be used for distributed computing
13. SQL is dynamic language because the users can submit the query amd manipulate the database dynamically and view output immediately.




## SQL data types:
1. char(n):
- It means fixed length string
- Here n represents maximum no. of characters
-. But if we store less than n characters in the column whose data type is char(n) then the extra characters are padded with spaces
e.g. if we have column named ename(10) and we store value 'abhay' which is having 5 characters, then extra 5 characters are padded with extra spaces.So there is unnecessary wastage of RAM memory.
- The minimum length of char is 1. The maximum length is dependent on page size(buffer size) of the table. If the size of char(n) exceeds page size then the char type is stored as clob means character large object.


2. varchar(n)
- It means variable length string
 - Here n represents maximum no. of characters
-. But if we store less than n characters in the column whose data type is varchar(n) then the extra characters are not padded with spaces
e.g. if we have column named ename(10) and we store value 'abhay' which is having 5 characters, then extra 5 characters are not padded with extra spaces.So there is nounnecessary wastage of RAM memory. So 'abhay' consumes 5 characters.
- The minimum length of char is 1. The maximum length is dependent on page size(buffer size) of the table. If the size of char(n) exceeds page size then the char type is stored as clob means character large object.


3. smallint
- It represent integers of smaller large
- Its range is 2^-15 to (2^15)-1
- Here values without decimal point/scale are allowed
- Here if we mention values with decimal point i.e. with scale then the digits after decimal point are truncated
e.g. If we store 4.9 in column of type small int, then value is stored as 4

4. int
- It represent integers of larger large
- Its range is 2^-31 to (2^31)-1
- Here values without decimal point/scale are allowed
- Here if we mention values with decimal point i.e. with scale then the digits after decimal point are truncated
e.g. If we store 4.9 in column of type small int, then value is stored as 4
- The max no. of digits i.e. precision allowed for int type is 38 digits

5. decimal(n,d)
1. Here it is used to store decimal point values
2. Here n represents max. precision means maximum no. of digits before and after the point
3. Here d represents scale. MEANS MAX. NO. OF DIGITS AFTER POINT.
4. e.g.
if column type is decimal(5,3) then allowed values are
4.89,41.899,4.8999(no error but here the last 9 is removed and value is stored 4.899)


78.8999 will give error because precision is exceed.


e.g.
decimal(4,2)
48.90(allowed), 4.899(stored as 4.89), 412.89(error)



6. numeric(n,d)
same as decimal

7.float:
It represents values with or without decimal point. But when we use data type float we don't mention format (n,d). We only mention precision. The max precision for float type is 64


8. date:
-it includes value which represents dates
- The date must be in format 'yyyy-mm-dd'
- year must be a number from 0 to 9999
- month must be number from 01 to 12
- date must be 1-31 depending on month

e.g.'2012-05-21'


9. timestamp:
1. It is of format 'hh:min:ss'
2. Here hh means hour which must be number from 0 to 23
3. min must be from 0 to 59
4. ss means seconds must be 0 to 59.9999
5. If we mention am or pm, then the format is considered as per 12 hour clock
5. If we don't mention am or pm, then the format is considered as by default 24 hour clock





## SQL Queries:
1. DDL(Data definition language)
This includes all queries related to structure of table in database. It doesn't include queries related to rows and manipulation of data

A. create
-It is used for creating a new table
-
syntax:
create table tablename(column1 datatype,column2 datatype...column datatype);

- Optionally we can mention constraints for one or more columns

e.g.
create table employee(eid int primary key,ename varchar(100),esalary float,emobno int unique not null);
primary key means that all values in that column must be unique and not null. We can define primary key for only 1 column. But unique can be applied for multiple columns. not null means null is not allowed. But only unique constraint still allows null values.


SQL> desc employee151;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 EID                                       NOT NULL NUMBER(38)
 ENAME                                              VARCHAR2(100)
 ESALARY                                            FLOAT(126)
 EMOBNO                                    NOT NULL NUMBER(38)

**desc query will provide information regarding structure of table means name of table, names of columns and their data types**






SQL> insert into department159 values(4,'it',23);
Here no error even if we have inserted extra value in did column of department159 table because it is primary key and not foreign key
