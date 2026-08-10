# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

<img width="1244" height="280" alt="image" src="https://github.com/user-attachments/assets/c24a841f-b7b3-47ac-b616-bb0fa3cb8b7a" />


```
sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);

```

**Output:**

<img width="1073" height="105" alt="image" src="https://github.com/user-attachments/assets/332eb5f8-b143-49a5-95f4-fd33a8bbb427" />


**Question 2**
---
<img width="390" height="179" alt="image" src="https://github.com/user-attachments/assets/02596da7-3cff-4e9e-ae1f-2bb78244a2fe" />


```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM Discontinued_products;

```

**Output:**

<img width="669" height="133" alt="image" src="https://github.com/user-attachments/assets/8de0097a-fbd5-4dfa-ade9-dabd5d38d8d9" />


**Question 3**
---
<img width="547" height="251" alt="image" src="https://github.com/user-attachments/assets/a892fe16-ca05-4e19-9384-d9480406bc3b" />


```sql
CREATE TABLE Employees (
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);

```

**Output:**

<img width="860" height="139" alt="image" src="https://github.com/user-attachments/assets/5e8fb2a9-0854-413e-b63e-1b6403087ca9" />


**Question 4**
---
<img width="833" height="238" alt="image" src="https://github.com/user-attachments/assets/88a341d4-3c2a-4277-b809-3a0e119680f3" />


```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;
ALTER TABLE Companies ADD COLUMN mobilenumber number;
ALTER TABLE Companies ADD COLUMN DOB Date;
```

**Output:**

<img width="1047" height="186" alt="image" src="https://github.com/user-attachments/assets/5de42bbe-7553-4c7a-8fc5-482889643bcb" />

**Question 5**
---
<img width="838" height="174" alt="image" src="https://github.com/user-attachments/assets/faac92a3-108f-430b-8939-23a95d280fa9" />


```sql
CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1050" height="112" alt="image" src="https://github.com/user-attachments/assets/97674fb3-4508-4d0f-abbe-52de111e5278" />


**Question 6**
---
<img width="1082" height="278" alt="image" src="https://github.com/user-attachments/assets/bd7b378f-2c1e-48b5-a1d4-4f63ae2d8b2e" />


```

CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10,2) NOT NULL,
    discount DECIMAL(10,2) NOT NULL DEFAULT 0,
    CHECK (
        list_price >= discount
        AND discount >= 0
        AND list_price >= 0
    )
);
```
**Output:**

<img width="1208" height="137" alt="image" src="https://github.com/user-attachments/assets/dd2a4d68-7f5a-4b4c-bdd6-daa18ec693ec" />

**Question 7**
---
<img width="1148" height="200" alt="image" src="https://github.com/user-attachments/assets/c9b3e5af-38a2-40a8-b3f6-ab22f46352ee" />


```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;
ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);

```

**Output:**

<img width="1234" height="139" alt="image" src="https://github.com/user-attachments/assets/cd206f16-02bc-49ae-bacd-fe8487862749" />


**Question 8**
---
<img width="828" height="197" alt="image" src="https://github.com/user-attachments/assets/e6c9e02a-eb44-4ca5-9b10-ad49e2693942" />


```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL UNIQUE,
    Price REAL NOT NULL CHECK (Price > 0),
    StockQuantity INTEGER NOT NULL CHECK (StockQuantity >= 0)
);

```

**Output:**

<img width="1109" height="181" alt="image" src="https://github.com/user-attachments/assets/e6d233de-7777-4cc2-9c4d-8a5d77f32f7a" />


**Question 9**
---
<img width="1169" height="261" alt="image" src="https://github.com/user-attachments/assets/778b7c53-c1d6-4d09-b00a-35dc681fe3a7" />


```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');

```

**Output:**

<img width="916" height="153" alt="image" src="https://github.com/user-attachments/assets/96319bd6-59c2-4dbb-ad8f-cffafce158da" />


**Question 10**
---
<img width="1090" height="243" alt="image" src="https://github.com/user-attachments/assets/29e3785a-4e8c-43d2-be4f-d30ecc1714a2" />


```sql
INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (106, 'Fitness Tracker', 'Wearables', NULL, NULL);
INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (107, 'Laptop', 'Electronics', 999.99, 50);
INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (108, 'Wireless Earbuds', 'Accessories', NULL, 100);



```

**Output:**

<img width="784" height="134" alt="image" src="https://github.com/user-attachments/assets/77a35b2e-65f9-48d2-91b5-d7612ff4d7bd" />



## RESULT

Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
