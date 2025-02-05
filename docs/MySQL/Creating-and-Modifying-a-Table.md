---
sidebar_position: 4
---

# Creating and Modifying a Table

Once you have created your database, you can proceed to use it. In this session, it is assumed that you have created a database called `sql_tutorial`, as shown in the section titled **MySQL Database: Creation, Verification, and Deletion**.

## 1. Selecting the Database

To make `sql_tutorial` the current database for your session using the following command:

```sql
USE `sql_tutorial`;
```

- **Explanation:**
  - This command sets the `sql_tutorial` database as the active database, allowing you to perform operations within it.

## 2. Defining Data Types

When creating a table, you need to define the data types for each column. Here are some common data types in MySQL:

| Data Type        | Description                          |
|------------------|--------------------------------------|
| `INT`            | Integer                               |
| `DECIMAL(m, n)`  | Decimal with precision                |
| `VARCHAR(n)`     | Variable-length string                |
| `BLOB`           | Binary Large Object                   |
| `DATE`           | Date                                  |
| `TIMESTAMP`      | Timestamp                             |

### Explanation of Data Types
- **INT**: Used for integers.
  
- **DECIMAL(m, n)**: Used for numbers with a fixed number of decimal points, where `m` is the total number of digits and `n` is the number of digits after the decimal point. 
  - *Example*: `DECIMAL(4, 3)` can represent values like `2.177`.

- **VARCHAR(n)**: A variable-length string, where `n` specifies the maximum length.
  - *Example*: If `VARCHAR(5)`, then "car", "taxi", "train" are valid entries.

- **BLOB**: Used for storing large binary objects, such as images or audio files.

- **DATE**: Stores date values in the format 'YYYY-MM-DD'.

- **TIMESTAMP**: Stores date and time values in the format 'YYYY-MM-DD HH:MM:SS'.

## 3. Creating the `student` Table

Here is an example of creating a table named `student` using the following command:

```sql
CREATE TABLE `student` (
    `student_no` INT PRIMARY KEY,  -- This sets `student_no` as the primary key
    `name` VARCHAR(50),
    `major` VARCHAR(25)
);
```

### Explanation of Table Structure
- **`student_no`**: An integer that serves as the primary key for the table.
- **`name`**: A variable-length string for the student's name.
- **`major`**: A variable-length string for the student's major field of study.

## 4. Verify Initial Table Structure

Check if your table was structured successfully using the following command:

```sql
DESCRIBE `student`;
```

The expected output is as follows:

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

## 5. Modifying the Table Structure

### 5.1 Adding the `score` Column

To add a new column named `score` using the following command:

```sql
ALTER TABLE `student` ADD `score` INT;
```

#### Verify Table Structure After Adding Column

Check the updated structure using the following command:

```sql
DESCRIBE `student`;
```

#### Expected Output After Adding `score`

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
| score      | int         | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

### 5.2 Changing the Data Type of `score`

To change the data type of the `score` column to `DECIMAL(3,2)` using the following command:

```sql
ALTER TABLE `student` MODIFY `score` DECIMAL(3,2);
```

#### Verify Table Structure After Changing Data Type

Check the updated structure using the following command:

```sql
DESCRIBE `student`;
```

#### Expected Output After Changing Data Type

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
| score      | decimal(3,2)| YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

### 5.3 Dropping the `score` Column

To remove the `score` column using the following command:

```sql
ALTER TABLE `student` DROP `score`;
```

#### Verify Table Structure After Dropping Column

Check the updated structure using the following command:

```sql
DESCRIBE `student`;
```

#### Expected Output After Dropping `score`

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

## 6. Dropping the Table

If you need to delete the table `student` using the following command:

```sql
DROP TABLE `student`;
```

- **Caution:** This action is irreversible, and all data within the table will be lost. Ensure you really want to delete `student` before running this command.