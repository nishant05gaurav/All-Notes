# MySQL:

### `Database`: 
- It is a collecction of data in a format that can be easily accessed 
- A software application used to manage our DB is called DBMS (Database Management System)
- There are two types of Databases:
  - Relational (Data stored in Tables)
  - Non-Relational (Data not stored in tables)

### `SQL`:
-  It is a programming language used to interact with the realtional databases.
-  It is used to store, manipulate and retrieve data fromn RDBMS
-  It is used to perform `CRUD` operation:
   -  **`Create`**: To create databases, tables, insert tuples in tables, etc
   -  **`Read`**: To read data present in the database
   -  **`Update`**: Modify already inserted data
   -  **`Delete`**: Delete database, table or specific data point/ tuple/ row or multiple rows
- SQL is not a case sensitive language  
  - eg: `select` is the same as `SELECT`

![alt text](https://imgur.com/lpU6mog.png)

### `SQL Data Types`:
- In SQL, data types define the kind of data that can be stored in a column or variable
![alt text](https://imgur.com/GPsDSXH.png)
- `CHAR` is for fixed length and `VARCHAR` is for variable length strings. Generally, `VARCHAR` is better as it only occupies necessary memory and works more efficiently

### `Types of SQL commands`:
- **`DQL`** (*Data Query Language*): 
  - It is used to retrieve data from databases (**SELECT**)
  - It is a subset of SQL that focuses on retreiving the data from databases
- **`DDL`** (*Data Definition Language*):
  - It is used to create, alter, rename, truncate and drop database tables, indexes, etc (**CREATE**, **DROP**, **ALTER**, **RENAME**, **TRUNCATE**)
  - It is a subset of SQL which is responsible for defining and managing the structure of databases and their objects
- **`DML`** (*Data Manipulation Language*):
  - It is used to modify the database (**INSERT**, **UPDATE**, **DELETE**)
  - These are the commands that manipulates the data within a database
- **`DCL`** (*Data Control Languag*e): 
  - It is used to grant & revoke permissions. (**GRANT**, **REVOKE**)
  - It focuses on the management of access rights, permissions and security-related aspects of a database system
  - It is used to control who can access the data, modify the data, or perform administrative tasks within a database
  - It is also an important aspect of database security which ensures that data remains protected and only authorised users have the necessary privilages
- **`TCL`** (*Transaction Control Language*):
  - It is used to manage transactions (**COMMIT**, **ROLLBACK**, **START TRANSACTIONS**, **SAVEPOINT**)
  - It deals with the management of transactions within a databse
  - It ensures data consistency, integrity, and reliability in a database 

### `Database related Queries`:

1. **Create Database**:
```sql
CREATE DATABASE dn_name;
CREATE DATABASE IF NOT EXISTS dn_name;
```
eg:
```sql
CREATE DATABASE IF NOT EXISTS college;
```

2. **Delete Database**:
```sql
DROP DATABASE dn_name;
DROP DATABASE IF NOT EXISTS dn_name;
```
eg:
```sql
DROP DATABASE IF NOT EXISTS college;
```

3. **Show Databases and Tables**:
```sql
SHOW DATABASES;
SHOW TABLES;
```

### `Table related Queries`:

1. **Create**
```sql
CREATE TABLE table_name(
    column_name1 datatype constraint,
    column_name2 datatype constraint
);
```
eg: 
```sql
CREATE TABLE student(
rollno INT PRIMARY KEY, name VARCHAR (50)
);
```
2. **Select & View ALL columns**
```sql
SELECT * FROM table_name;
```
eg: 
```sql
SELECT * FROM student;
```
3. **Insert**
```sql
INSERT INTO table_name
(colname1, colname2)
VALUES
(col1_v1, col2_v1),
(col2_v2, col2_v2),
```
eg: 
```sql
INSERT INTO student
(rollno, name)
VALUES
(101, "ABC"),
(102, "DEF");
```