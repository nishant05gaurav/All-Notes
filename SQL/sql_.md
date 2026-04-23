- **Data**
  -  It is a collection of raw facts and figures that do not have meaning by themselves
  -  When data is *processed*, *structured*, or *related*, it becomes **Information**
-  **Database**: It is an organised collection of related data stored electronically, so that it can be easily *accessed*, *managed*, and *updated*
-  It's not recommended to store the data in **files** because:
   -  *Data Redundancy* (Same data repeated in multiple files)
   -  *Inconsistency* (Updates not reflected everywhere)
   -  *No Security* (Anyone can modify files)
   -  *No Concurrency* (Multiple users cause conflicts)
- **DBMS**: Database Management System is a software that allows users to *create*, *store*, *retrieve*, *update*, and *manage* databases efficiently.
- DBMS acts as an interface between users and the databases (**User → DBMS → Database**)
---
## SQL
- **SQL**(*Structured Query Language*) is a standard language used to communicate with relational databases.
- SQL can do:
  - Create databases and tables
  - Insert, update, delete data
  - Retrieve data using queries
  - Control access to data
- **RDBMS**:
  - Relational Database Management System 
  - Software that enables us to implement designed relational model
  - E.g., MySQL, MS SQL, Oracle, IBM, etc.
  - Table/ Relation is the simplest form of data storage object in R-DB
  - *MYSQL* is an open-source RDBMS, and it uses SQL for all CRUD operations
- **MYSQL** used client-server model, where client is CLI or frontend that used services provided by MySQL server
### DDL 
- DDL stands for Data Definition Language that defines relational schema
- **CREATE**: It is used to define a new database object
   1. **CREATE DATABASE**:
   ```sql
   CREATE DATABASE database_name;
   <!-- Example -->
   CREATE DATABASE student;
   ```
   
   2. **CREATE TABLE**:
   ```sql
   CREATE TABLE table_name (
    column_name datatype constraints
    );
   <!-- Example -->
   CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50)
    );
   ```
- **ALTER**: It is used to modify an existing table structure.
   1. **ADD Column**:
   ```sql
   ALTER TABLE students
   ADD email VARCHAR(50);
   ```
   2. **MODIFY/ ALTER Column**:
   ```sql
   ALTER TABLE students
   MODIFY name VARCHAR(100);
   ```
   3. **DROP Column**:
   ```sql
   ALTER TABLE students
   DROP COLUMN email;
   ```
   4. **RENAME Column**:
   ```sql
   ALTER TABLE students
   RENAME COLUMN department TO branch;
   ```
- **DROP**: Removes the entire database object permanently
   ```sql
   DROP TABLE students;
   ```
- **TRUNCATE**: Deletes all rows from a table without deleting the structure
   ```sql
   TRUNCATE TABLE students;
   ```
- **RENAME**: Renames a database object
   ```sql
   RENAME TABLE students TO learners;
   ```

### DML
- It stands for Data Modification Language that is used to perform modifications in the Database
1. **INSERT COMMAND**:
```sql
    <!-- INSERT a Single Row: The number and order of values must match table columns -->
    INSERT INTO table_name
    VALUES (value1, value2, ....);
    <!-- Example -->
    INSERT INTO students
    VALUES (101, 'Nishant', 'CS');

    <!-- INSERT With Column Names -->
    INSERT INTO table_name (column1, column2)
    VALUES (value1, value2);
    <!-- Example -->
    INSERT INTO students (student_id, name)
    VALUES (102, 'Sushant', 'CS');

    <!-- INSERT Multiple  Rows: Faster and common in batch processing -->
    INSERT INTO students (student_id, name, department)
    VALUES
    (103, 'Vigyat', 'IT'),
    (104, 'Krishna', 'IT');
```
2. **UPDATE COMMAND**: Modifies existing records in a table.
```sql
    <!-- UPDATE With WHERE Clause -->
    UPDATE table_name
    SET column = value
    WHERE condition;  <!-- Without WHERE, every row is updated. -->
    <!-- Example -->
    UPDATE students
    SET department = 'AI'
    WHERE student_id = 104;

    <!-- UPDATE Multiple Columns -->
    UPDATE students
    SET department = 'DS', name = 'Satish'
    WHERE student_id = 103;

    <!-- Always run SELECT before UPDATE as: SELECT * FROM students WHERE student_id = 103;-->
```
3. **DELETE**: Removes existing records from a table.
```sql
    <!-- Conditional DELETE -->
    DELETE FROM table_name
    WHERE condition;
    <!-- Example -->
    DELETE FROM students 
    WHERE student_id = 103;

    <!-- DELETE all Records -->
    DELETE FROM students;  <!-- Deletes data row by row; Slower than TRUNCATE; Can be rolled back(with transactions) -->
```

### DQL
- It stands for Data Query Language
- **SELECT**: Retrieves data from one or more tables without modifying it
    ```sql
    SELECT * FROM table_name;
    <!-- Example -->  
    SELECT * FROM students;

    SELECT column1, column2
    FROM table_name;
    <!-- Example -->
    SELECT student_id, name
    FROM students;  
    ```
- **WHERE Clause**: It filters rows based on condition
  ```sql
    SELECT columns
    FROM table_name
    WHERE condition;
    <!-- Example -->
    SELECT *
    FROM students
    WHERE department = 'CS';

    <!-- Using Comparision Operators -->
    SELECT name
    FROM students
    WHERE marks >= 80;

    <!-- Logical Operators -->
    WHERE department = 'CS' AND marks > 75;
    WHERE department = 'CS' OR department = 'IT';
    WHERE NOT department = 'HR';
  ```
- **DISTINCT**: Removes duplicate rows from result set.
    ```sql
    SELECT DISTINCT column
    FROM table_name;
    <!-- Example -->
    SELECT DISTINCT department
    FROM students;
    ```
- **ORDER BY**: Sorts the result set
  ```sql
    SELECT columns
    FROM table_name
    ORDER BY column [ASC|DESC];
    <!-- Example -->
    SELECT name, marks
    FROM students
    ORDER BY marks DESC;

    <!-- Multiple Columns -->
    ORDER BY department ASC, marks DESC;
  ```

### AGGREGATE Functions:
- Aggregate functions operate on multiple rows and return a single summarised value
- **COUNT()**: Returns the number of rows
  ```sql
  SELECT COUNT(column_name)
  FROM table_name;

  <!-- COUNT(*): Counts all rows, Faster inmost DBMS -->
  ```
- **SUM()**: Returns the total of numeric values
  ```sql
    SELECT SUM(column_name)
    FROM table_name;

    <!-- Works only on numeric columns -->
    <!-- NULL values all ignored -->
  ```
- **AVG()**: Returns the average (mean) value
    ```sql
    SELECT AVG(column_name)
    FROM table_name;

    <!-- AVG = SUM / COUNT (non-NULL rows) -->
    <!-- NULL values are ignored -->
    ```
- **MIN() & MAX()**
  ```sql
    SELECT MIN(column), MAX(column)
    FROM table_name;
  ```

- **GROUP BY & HAVING**:
  - *GROUP BY* allows us to: Divide rows into groups & apply aggregate functions per group
  - *GROUP BY* groups rows that have the same values in specified columns
    ```sql
    SELECT column, aggregate_function(column)
    FROM table
    GROUP BY column;
    <!-- Example -->
    SELECT department, AVG(marks)
    FROM students
    GROUP BY department;

    SELECT department, COUNT(*)
    FROM students
    WHERE marks >= 60               <!-- WHERE filters rows -->
    GROUP BY department;            <!-- GROUP BY forms groups -->
    ```
    - *HAING* filters groups, not rows as WHERE cannot filter aggregate results
        ```sql
            SELECT column, aggregate 
            FROM table
            GROUP BY cillumn
            HAVING condition;
            <!-- Example -->
            SELECT department, COUNT(*)
            FROM students
            GROUP BY department
            HAVING COUNT(*) > 10;   <!-- Shows only departmets with more than 10 students-->
        ```

### Constraint
- A constrain is a rule applied to a column or table that restricts the type of data that can be stored
- It's important because:
  - Duplicate records cannot appear
  - invalid refrences are not stored
- **NOT NULL**: Ensures a column cannot contain *NULL* calues
    ```sql
    CREATE TABLE students (
        student_id INT NOT NULL,
        name VARCHAR(50) NOT NULL
    );
    ```
- **UNIQUE**: Ensures all values in a column are distinct
  ```sql
    CREATE TABLE users (
        email VARCHAR(100) UNIQUE
    );

    <!-- Characteristics: Allows NULL and prevent duplicates -->
  ```
- **PRIMARY KEY**: Uniquely identifies each record in a table
  ```sql
    CREATE TABLE students (
        student_id INT PRIIMARY KEY,
        name VARCHAR(50)
    );

    <!-- Composite PRIMARY KEY: Usedin junction tables -->
    PRIMARY KEY (student_id, course_id);
  ```
- **FOREIGN KEY**: Created a relationship between tables and enfores referential integrity
  ```sql
    CREATE TABLE enrolments (
        student_id INT,
        FOREIGN KEY (student_id) REFERENCES students(student_id)
    );

    <!-- Foreign keys protect relationships, not performance -->
  ```
- **CHECK CONSTRAINT**: Ensures values meet a specific condition
  ```sql
    CREATE TABLE students (
        marks INT CHECK (marks >= 0 ANDmarks <= 100)
    );
  ```
- **DEFAULT CONSTRAINT**: Assigns a default value if no value is provided
  ```sql
    CREATE TABLE orders (
        status VARCHAR(20) DEFAULT 'PENDING'
    );
  ```

### JOINS
- RDBMS are relational in nature, we refer to other tables to get meaningful outcomes
- Function Key are used to do reference to other table
- **INNER JOIN**: Returns only matchinng records from both tables
  ```sql
    SELECT columns
    FROM table1
    INNER JOIN table2
    ON condition;
    <!-- Example -->
    SELECT s.name, c.cours 
    FROM students s
    INNER JOIN courses c
    ON s.student_id = c.student_id;
  ```
- **LEFT JOIN**: Returns all rows from left table; Matching rows from right table; NULL where no matching exists
  - *LEFT JOIN* is often used to detect gaps in data 
  ```sql
    SELECT columns
    FROM table1
    LEFT JOIN table2
    ON condition;

    <!-- Example -->
    SELECT s.name, c.course
    FROM students s
    LEFT JOIN courses c
    ON s.student_id = c.student_id;
  ```
- **RIGHT JOIN**: Returns all rows from right table; Matching rows from left table
  - *RIGHT JOIN* is logically equivalent to lEFT JOIN with reversed tables
  - Mostlt professionals prefer LEFT JOIN only 
  ```sql
    SELECT s.name, c.course
    FROM students s
    RIGHT JOIN courses c
    ON s.student_id = c.student_id;
  ```

- **FULL JOIN**: Returns a resulting table that contains all data when teher is a match om left or righ table data 
  - Use Case: Data reconcilliation; Comparing datasets
  ```sql
    SELECT s.name, c.course
    FROM students s
    FULL JOIN courses c
    ON s.student_id = c.student_id;
  ```

- **SELF JOIN**: A table joined with itself
  - *RIGHT JOIN* is logically equivalent to lEFT JOIN with reversed tables
  - Mostlt professionals prefer LEFT JOIN only 
  ```sql
    SELECT e.name AS employee, m.name AS manager
    FROM employees e
    LEFT JOIN employees m
    ON e.manager_id = m.employee_id;
  ```

### SUBQUERY:
- A subquery is a queery that provides input to another query
  ```sql
    SELECT column
    FROM table  
    WHERE column operator (SELECT column FROM table);

    <!-- Example -->
    SELECT name
    FROM students
    WHERE marks > (
        SELECT AVG(marks)
        FROM students
    );

    SELECT name
    FROM students
    WHERE department IN (     
        SELECT department
        FROM students
        GROUP BY department
        HAVING COUNT(*) > 50
    );
  ```
- *Subquery Operator*:
  - **IN**: Matches any value in the subquery result
    ```sql
    WHERE department IN (subquery)
    ```
  - **ANY**: Condition true if any one value matches.
    ```sql
    WHERE marks > ANY (subquery)
    ```
  - **ALL**: Condition true only if all values match.
    ```sql
    WHERE marks > ALL (subquery)
    ```
- *Correlated Subquery*: A corelated subquery depends on the outer query for its values; It executes once per row
  ```sql
    <!-- Find students whose marks are higher than the average of their department -->
    SELECT s1.name
    FROM students s1
    WHERE s1.marks > (
        SELECT AVG(s2.marks)
        FROM students s2
        WHERE s2.department = s1.department
    );
  ```

### SET Operations
- Combine result of multiple SELECT queries into a single result set
- *Rules*:
  - Same number of columns
  - Compatible data types
  - Same column order 
  - Columns names take from first SELECT
- **UNION**: Combine results of two wueries and remove duplicates
  ```sql
    SELECT column FROM table1
    UNION
    SELECT column FROM table2;
    <!-- Example -->
    SELECT email FROM customers
    UNION
    SELECT email FROM subscribers;
  ```
- **UNION ALL**: Combines results without removing duplicates
  ```sql
    SELECT column FROM table1
    UNION ALL
    SELECT column FROM table2;
  ```
  - Use `UNION ALL` unless deduplication is expliciitly required
- **INTERSECT**:Returns only common rows present in both result sets
  ```sql
    SELECT column FROM table1
    INTERSECT
    SELECT column FROM table2;
  ```
- **EXPECT**: Returns rows present in first query but not in second
  ```sql
    SELECT column FROM table1
    EXPECT
    SELECT column FROM table2;
  ```

### VIEWS
- A view is a virtual table created using a SELECT query
  - It does not store data
  - It stores the query definition
  - Data is fetched dynamically from base tables
- *Creating a View*:
  ```sql
    CREATE VIEW view_name AS
    SELECT columns
    FROM table
    WHERE condition;
    <!-- Example -->
    CREATE VIEW cs_students AS
    SELECT student_id, name
    FROM students
    WHERE department = 'CS';
  ```
- *Limitations*:
  - Most views are read-only
  - Performancedepends on base query
  - Cannot always insert/ update through views
  
### INDEXES:
- An index is a data structure that speeds up data retrieval
  ```sql
    CREATE INDEX index_name
    ON table_name(column_name);
  ```

### TRANSACTIONS:
- A transaction is a sequence of one or more SQL operations that are treated as a single logical unit of work
- **COMMIT**: Permanently saves all changes made in the current trancsaction
> COMMIT
- **ROLLNACK**: Undoes all changes made since the last COMMIT.
> ROLLBACK;
- **SAVEPOINT**: Creates a checkpoint inside a transaction
> SAVEPOINT sp1
> ROLLBACK TO sp1;   <!-- Rollback to savepoint-->

### DCL
- Data Control Language
- DCL controls access; it does not manage identity
- **GRANT**: Gives specific privileged to users or roles
  ```sql
    GRANT pribilege
    ON object
    TO user;
    <!-- Example -->
    GRANT SELECT
    ON students
    TO app_user;
   ```
- **REVOKE**: Removes previously granted privileges
  ```sql
    REVOKE privilege
    ON object
    FROM user;
    <!-- Example -->
    REVOKE INSERT
    ON students
    FROM app_user;
  ```
- *Read-Only User*: 
> GRANT SELECT ON students TO report_user;
- *Application User*:
> GRANT SELECT, INSERT, UPDATE ON orders TO app_user;
- *View-Based Security*:
> GRANT SELECT ON cs_students TO intern_user;

### STRING FUNCTIONS:
- **UPPER() & LOWER()**: Convert text case
  ```sql
    SELECT UPPER(name) FROM students;
    SELECT LOWER(email) FROM users;
  ```
- **LENGTH()**: Returns number of characters
  ```sql
    SELECT LENGTH(name) FROM students;
  ```
- **SUBSTRING() / SUBSTR()**: Extracts part of a string.
  ```sql
    SELECT SUBSTRING(name, 1, 4) FROM students;
  ```
- **CONCAT()**: Joins strings
  ```sql
    SELECT CONCAT(first_name, ' ', last_name) AS full_name
    FROM employees;
  ```

### NUMERIC FUNCTIONS:
- Used for calculations and rounding
- **ROUND()**:
  ```sql
     SELECT ROUND(AVG(marks),2) FROM students;
  ```
- **CEILING() & FLOOR()**: 
  ```sql
    SELECT CEILING(4.2);   -- 5
    SELECT FLOOR(4.8);    -- 4
  ```
- **ABS()**:
  ```sql
    SELECT ABS(-50);
  ```
- **MOD()**
  ```sql
  SELECT MOD(10, 3);  -- 1
  ```

### DATE & TIME FUNCTIONS: 
- **CURRENT_DATE? CURRENT_TIMESTAMP**:
  ```sql
    SELECT CURRENT_DATE;
    SELECT CURRENT_TIMESTAMP;
  ```
- **EXTRACT()**:
  ```sql
    SELECT EXTRACT(YEAR FROM order_date)
    FROM orders;
  ```

### NULL-HANDLING FUNCTIONS:
- **COALESEC()**: Returns first not-NULL value
  ```sql
    SELECT COALESCE(phone, 'Not Provided')
    FROM users;
  ```
- **IFNULL()/ NVL()**: Always handle NULLs explicitly in reports
  ```sql
    SELECT IFNULL(bonus, 0)
    FROM employees;
  ```