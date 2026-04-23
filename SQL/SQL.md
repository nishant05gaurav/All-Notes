```sql
system cls;
```
- Used for clearing the screen 
```sql
SELECT DATABASE();
```
- Shows the table in which you are working
```sql
SHOW DATABASES;
```
- Listing all the databases
```SQL
SHOW Tables;
```
- Listing all tables
```sql
CREATE DATABASE <db_name>;
```
- Used for creating database
```sql
DROP DATABASE <db_name>;
```
- Used for deleting a database
```sql
CREATE TABLE <tb_name>
(
    id INT,
    name VARCHAR(20)
);
```
- Used for creating a Table
```sql
DESC <tb_name>
```
- Used to describe your table
```sql
ALTER TABLE <tb_name>
ADD COLUMN <column_name> datatype;
```
- Used to add extra column in an existing table
```sql
ALTER TABLE <tb_name>
DROP COLUMN <column_name>;
```
- Used to delete an existing column from a Table 
```sql

```
- Used to list all the tables (if present)



---

- SQL (Structured Query Language) is a standard language for accessing and manipulating databases
- SQL can execute queries, retrieve data, insert data, update data, delete data, create new databases, create new table.
- RDBMS (Relational Database Management System) is the software that actually stores, manages, and secures data. It organises information into related tables (rows and columns) and handles all the complex background work.
- Every table is broken into smaller entities called fields (a column in a table that maintains specific informations)
- 