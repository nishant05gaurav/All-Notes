## Data
- Collection of raw, unorganized facts and details like observations, figures, symbols, facts, etc
- Stored in the form of bits and bytes
- It has no significance by itself

## Information
- It is processed, interrupted, organized, and structured data
- Extracted from the data by analyzing and interpreting pieces of data

## Data vs Information

| **Data** | **Information**|
| -------  | --------- |
| Collection of facts | Put those facts into context |
| Raw and unorganized | Organized |
| Typically come in the form of graphs, numbers, figures, and statistics | Typically presented through words, language, and ideas |
| Doesn't depend on information | Depend on information |
| Insufficient for decision-making  | Make decision based on information |

## Database
- It is an electronic place/system where data is stored in a way that it can be easily accessed, managed, and updated
- It is the collection of related data that represent some real-world entities
- If some changes are there in the real-world entities then the same should be reflected in the database
- To make real use of data, we need a Database management system (DBMS)

## DBMS
- `EF Codd` is the father of DBMS
- It is a software used to create, manipulate, and delete data
- It is a collection of interrelated data and a set of programs to access those data
- The collection of data usually referred to as the database, contains information relevant to an enterprise
- **Primary Goal**:
  -  Store and retrieve database information i.e, both convenient and efficient
- It is a database with all the software and functionality.
- By using this we can perform operations such as addition, updation, deletion, and accessing of data

## Rules followed by DBMS during transaction
DBMS follows ***ACID*** rule during transaction and these are as follows:
1. **Atomicity**: If transaction gets fullfill then its get add back to DBMS else it gets roll back
2. **Consistency**:
  - Follows rules and constrains
  - Changes from one valid state to another
  - Maintains Data Integrity
    > Data Integrity: The process of ensuring that data is accurate, complete, consistent, and valid
3. **Isolation**:
  - Transactions are independent
4. **Duraible**:
  - Not deleted unless we did it
  - Change persists

- Understand using example of transaction:
  - Atomicity: Lets say we are performing a transaction in Gpay, if the transaction gets successful then and only then its getting add back to DBMS or else it gets rolled back
  - Consistency: Here, using consistency we are drafting the information in specific columns like name in alphabets and amounts in balance
  - Isolation: Performing transactions from two different bodies like Gpay and PhonePay
  - Duriable: Every transactions are written either it is done or not

## Disadvantages of using File System
1. **Data Redundancy and Inconsistency**: Storing the same data in multiple locations leads to unnecessary duplication, and if updates are made to only one instance, inconsistencies arise.
2. **Difficulty in Accessing Data**: Retrieving specific data can be complex and inefficient due to the lack of structured queries.
3. **Data Isolation**: Related data stored in different files or locations is challenging to access and retrieve.
4. **Isolation Problem**: Ensuring the accuracy, consistency, and reliability of data across isolated files is difficult.
5. **Atomicity Problem**: Incomplete operations can lead to partial updates, leaving data in an inconsistent state.
6. **Concurrent Access Anomalies**: Simultaneous access or modifications by multiple users can result in conflicts and data corruption.
7. **Security Problem**: File systems lack advanced security measures, making it harder to control access and protect sensitive information.

## OLAP
- OLAP (Online Analytical Processing) is type of data processing system that is designed for complex queries and analysis of data
- It is used for data mining, business intelligence, and decision support systems
- It is optimized for reading data, enabling users the analysis of data onto different prespective and extract meaningful insights
- **Characteristics**:
  - *Data Structure*: Organized in a multi-dimensional model (star schema, snowflake schema) that allows easy slicing and dicing of data
  - *Data Volume*: Handles large volume of historical data
  - *Speed*: Optimized for fast query performance, especially for complex queries
  - *Use Cases*: Reporting, forecasting, trend analysis, budgeting, and data mining

## OLTP
- OLTP (Online Transaction Processing) is a type of data processing system that is designed for the managment of transactional data
- It supports day-to-day operations by handling a large number of short, atomic transactions
- These are optimized with writnig data, ensuring data integrity and consistency
- **Characteristics**:
  - *Data Structure*: These are often normalized to reduce data redundancy and ensure data integrity
  - *Data Volume*: Handles current real-time data and often has a large number of short transactions
  - *Speed*: Optimized for quick processing of individual transactions, ensuring immediate updates to the database
  - *Use Cases*: Customer relationship management (CRM), e-commerce systems, online banking, and point-of-sale (POS) system

| Key Diff | OLAP | OLTP | 
| ------- | ------- | -------- |
| *Functionality*   | Data analysis and reporting | Data entry and retrieval for day-to-day operations |
| *Data Structure*  | Allows slicing and dicing of data  | Relational and higly normalized |
| *Query Complexity* | Complex (joins, aggregations, and data analysis) | Simple (insertions, updates, and deletions) |
| *Data Volume* | Large volumes of historical data  | Current, real-time data  |
| *Performance* | Optimized for query performance | Optimized for transaction performances |

## ER Diagram
- Introduced by `Dr. Peter Chan` in 1976
- It is a high-level data model, used to define data elements and their relationship
- A non-technical design method works on conceptual level based on the perception of real world
- Consists of basic objects called `entity` and a `relationship` among their objects and `attributes` that defines their properties
- Free from ambiguties and provides a standard and logical way of visuaizing data
- Basically, it is a diagramatical represenataion that are easy to understand even by non-technical users
![alt text](https://imgur.com/jIA80Ns.png)

## Entity
- An entity is a thing or an object in the real world that is distingaishable from other objects based on the values of the attributes it posseses
- class is same as object and entity as ID (HTML/CSS)
- **Types**:
  - *Tangible*: Entities which physically exist in real world. eg: Car, Pen, Banklocker
  - *Intangible*: Entities which exists logically. eg: Account
- `Weak Entity`: An entity that depends on another entity is called a weak entity. It does not contain any key attribute of its own
  - It avoids data duplication caused by duplicating these of a strong entity
- `Strong Entity`: An entity set that contains sufficient attributes to uniquely identify all its entities
  - Primary keys exist in it
- An Entity cannot be represented in an er diagram as it is only an instance or schema

### `Entity set`:

- Collection or set of same types of entities i.e, that share same properties or attributes
- Entity set is surrounded by rectangle in er diagram
- Entity can be represented in an relational model by row/ type/ record
- Entity set is represnted by table in relational model
- In total-entity set, if we find an entity which don't participate at a single time then side takes `Partial Participation` (or) If there is minimum cardinality set as zero then that entity set is not bonded to take participation in relationship and that side is having `Partial Participation`
- `Total Participation`: Each entity set gets participated and minimum partiality is greater than 1
  - It is represented by **double line**
  - Through line method, we are unable to find the maximum bound. So, we use bracket form.

### `Attribute`:

- These are the units that describe the characteristics of entites
- For each attribute there is a set of permitted values called domain
- In er diagram, represented by ellipse or oval, while in relational model by separate column
  ![alt text](https://imgur.com/4xnx42M.png)
- A relationship can also possible among those entity which lie on sinlge entity

### `Relationship`:

- It is an association between two or more entites of same or different entity set
- No representation in ER Diagram as it is an instance or data
- In relational model, reprsented by either using a row in a table
  ![alt text](https://imgur.com/12qZlXV.png)
- `1:1` - At most have 1 relation and its not necessary to participate
- `1:M ; M:1`: - At most n participation
![alt text](https://imgur.com/Zwiujye.png)
- Every **1:1** is **M:1** and **1:M**

### `Relationship set`:

- A set of similar type of relationship
- Represented using a diamond or rhombus in ER Diagram
- Represnted using a separate table or by separate column (foreign key)
- Every relationship type has three component:
  - Name
  - Degree
  - Carditionally Ratio/ Participation Constrains
- A relationship can also possible among those entity which lie on single entity
  ![alt text](https://imgur.com/na491D9.png)

### `Degree of a Relationship Set`:

- Number of entity set participating in the relationship set
- Mostly these are binary
- `Types`:
  ![alt text](https://imgur.com/46ZICnf.png)

### `Cardinalities / Cardinality Ratio`: (`MAPPING`)

- Expresses the number of entities to which other entity can be related (via a relationship)
- NOTE:
  - In case of one-to-one. One entity relates to at most one entitty of other set. So, it may be possible that some entity do not relate to any one
- `Cardinality Constraint`: Maximum number of relationship instances in which an entity can participate

### `Participation Constraints`:
- It satisfies the maximum and minimum number of relationship instances that each entity can/ must participate in
- `Types`:
  - `Max-Cardinality`: Maximum number of times an entity can occur in relationship 
  - `Min-Cardinality`: Minimum number of times an entity can occur in relationship
- `Partial Participation`: When  min-cardinality is zero (c = 0)
- `Total Participation`: When  min-cardinality is greater than zero (c > 0)
![alt text](https://imgur.com/Pt3ceCX.png)

### `Functional Dependency`:

- Relationship b/w two attributes (Primary key & Non-key)
- If we have two set of attributes (alpha, beta) and they are in functional dependecy between them then, through alpha we can find the values of beta
  - We can only get one value of beta for the same value of alpha
    ```
    eg:
      a --> 1
      b --> 2
    ```
    It is many-to-one
  - We can get multiple values of beta for different values of alpha
    ```
    eg:
     a --> 1
     b --> 2
     a --> 5 -->(X)
    ```
    - Here, f(a) = 1 then f(a) can not be equal to 5
    - Its one-to-one
- `Types`:
  ![alt text](https://imgur.com/pDNbW7x.png)

### **Question on Functional Dependency**:

- Find which is not valid dependency:
  ![alt text](https://imgur.com/D3Lnebe.png)
- `NOTE`: when (α --> β)
  - If all α's are unique then we don't need to check as all are correct
  - If all β's are same then we don't need yo check as all are correct

### `Armstrong Axiom`: (`CLOSURE`)
- Attribute closure/ Closure on attribute set/ closure of attribute set
- It can be defined as a set of attributes which can be functionally determined from it 
- Denoted by `F+`
![alt text](https://imgur.com/yBYXcJi.png)

### `Armstrong Axioms`: These are the basic rules of functional dependencies
![alt text](https://imgur.com/x4H9Q13.png)
- Union and Deecomposition are always used in right side of the expression

### `Comparing Two Functional Dependencies`:
1. Calculate closure for both set of attributes
2. Use the Opposite Set for Validation:
   - Compute the closure by referencing dependencies from the opposite set 
      - As: Calculate the closure of attributes in F, using G’s dependencies, and vice versa.
3. Repeat the Process for the Other Side:
   -  Calculate the closure oof others also
4. Final Comparison:
   -  If the closures match in both directions (F using G and G using F), the two sets are equivalent.
   -  If one set's closure is a subset or superset of the other, it indicates a dependency relationship between the two sets.

![alt text](https://imgur.com/CFBfL1i.png)
```md
- If F ⊆ G: F’s functional dependencies are a subset of G’s.
- If F ⊇ G: F’s functional dependencies are a superset of G’s.
- If F ≡ G: F and G are equivalent in terms of their functional dependencies.
- If F ≠ G: F and G have different functional dependencies.
```
### `Irreducible set of Fd(conical Form)`:
- In the given set of Fd, there exist some redundant element, and we need to remove them
- `Redundant`:Their presence and existance don't affect the capability of the Fd
- There are three cases of Redundancies:
  - On the left side of the Fd
  - On the right side of the Fd
  - Entire set 
- Steps: 
  - First write separately using Decomposition rule wherevver more than 1 attribute is present on the right hand side
    - Now the possibility of redundancy in right hand side not exist b/c we have decomposed them
  - Calculate the closure of every element on the left hand side
    - There is a catch that you have to do this process twice, on the second go you need to  ignore the fd of the first attempted 
    - Compare the two:  
      - if the closure comes different it says this dependecny is essential
      - if the closure comes same it says this dependecy is redundant and you need to clear it
        - while clearing it you have to neglect it fully also in cases of finding other attributres
    - After that write the rest:
    - Thereafter you only need to check the dependecies of that having more than 1 attribute.
      - this time by calculating the closure of all 
      - After that calculating the closure of each separately
        - if the values comes ssame in either on (i.e, in each attribute) with the closure (as a whole). Then this dependency is redundant
- for the same set of fd there exists more than 1 conical form and that depends on order you are performing the operation

### `KEYS`:
- **Need**: For the retrival of data from the databse.
- Key (either single/ set of attribute) must identify the row/ tupple of the database
- Key is a set of attribute which uniquely identify the row and a tupple in a relationship table
- `Key` ≡ `SuperKey`; Its closure always give all the attributes

### `Candidate Key`: 
- It is an efficient version of superkey
- A superkey is called a candidate key whose proper sub-set is not a superkey
- It can be multiple is numbers
![alt text](https://imgur.com/4Vb8OBm.png)
- Every Candidate Key is not a SuperKey but to become a Candidate Key, it should be SuperKey. 

### `Primary Key`:
- It is that candidate key which is selected by the administrator as the primary mean to identify tuples
- It's number is only one 

![alt text](https://imgur.com/kY0tFQe.png)
![alt text](https://imgur.com/V9IsB1j.png)

### `NORMALIZATION`:
- Normalization is a process to remove data-redundancy
 
![alt text](https://imgur.com/wdinXcK.png)
- `Redundancy vs Inconsistemcy`: 
  - When some data is stored multiple times in a database, called **Redundancy**
  - When the values of these data are different in different places then it's called **Inconsistency**

- `Solve Redundancy`:
  - It's easier to gather data in one place than to create separate tables.
  - Make sure to create tables in such a way that each table contains data that is directly related to each other.
    - For example, one table should contain a single idea
  - As one paragraph contains a single idea similarly are table must contain direct and main data about an entity
  - Normalisation (decomposition of tables) of table is done of the basic of functional dependency

### `1 Normal Form`:
- A table is said to be in a 1 NF, if every cell contain atomic value
- Here, `multi-valued` attribute is not allowed
- For this we need to repeat each value in each column
- When we convert ER Diagram to Relational Model, for every multivalued attribute you should have an independent table
- If there is a relational schema, then the table is said to be in 1NF
- Every column should contain the value of same domain and every column should have different name

### `2 Normal Form`:
- A table is said to be in **2 NF** if:
  - Must be in 1 NF
  - No Partial Dependency
![alt text](https://imgur.com/MqurwVG.png)
- `Prime Attribute`: Those attribute which are a part of Candidate Key
- `Non-Prime Attribute`: Those attribute which are not a part of Candidate Key
- If an attribute is a part of  any one of the CK, said to be prime attribute. Here, C only depends on B (not to prime attribute AB) So, it's partial dependent. 
- `Partial Dependency`: When a non-prime attribute instead of depending on the entire CK, it depends only on the part of CK
- In the above diagram , C is non-prime it should depend on whole PK, but it depends only on its part
- **Problem with 2NF**: At run-time if its value become NULL, at that time you cannot calculate C

### `Conversion to 2NF`:
- Make a table that only contains PK and with those attribute who can be calculated using it
  - R1(A B D)
- Make another table with those which are making prime attribute 
  - R2(B C)
- Always make a separate table for PK 
  - R3(A B C)
