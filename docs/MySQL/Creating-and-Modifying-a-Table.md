---
sidebar_position: 4
---

# Creating and Modifying a Table

In this section, we will explore how to create and modify a table in your MySQL database. 

## 1. Prerequisites

Before you begin, ensure you have **Database Created**. You should have a database called `sql_tutorial`, as demonstrated in the section titled [**MySQL Database: Creation, Verification, and Deletion**](/docs/MySQL/Creating-Database).

## 2. Selecting the Database

To make `sql_tutorial` the current database for your session, use the following command:

```sql
USE `sql_tutorial`;
```

### 2.1 Explanation:
- This command sets `sql_tutorial` as the active database, allowing you to execute commands within it.

## 3. Defining Data Types

When creating a table, you must define the data types for each column. Here are some common data types in MySQL:

| Data Type        | Description                          |
|------------------|--------------------------------------|
| `INT`            | Integer                              |
| `DECIMAL(m, n)`  | Decimal with precision               |
| `VARCHAR(n)`     | Variable-length string               |
| `BLOB`           | Binary Large Object                  |
| `DATE`           | Date                                 |
| `TIMESTAMP`      | Timestamp                            |

### 3.1 Explanation of Data Types

- **INT**: Used for integers.
  
- **DECIMAL(m, n)**: Used for numbers with a fixed number of decimal points, where `m` is the total number of digits and `n` is the number of digits after the decimal point. 
  - *Example*: `DECIMAL(4, 3)` can represent values like `2.177`.

- **VARCHAR(n)**: A variable-length string, where `n` specifies the maximum length.
  - *Example*: If `VARCHAR(5)`, then "car", "taxi", and "train" are valid entries.

- **BLOB**: Used for storing large binary objects, such as images or audio files.

- **DATE**: Stores date values in the format 'YYYY-MM-DD'.

- **TIMESTAMP**: Stores date and time values in the format 'YYYY-MM-DD HH:MM:SS'.

## 4. Creating the `student` Table

To create a table named `student`, use the following command:

```sql
CREATE TABLE `student` (
    `student_no` INT PRIMARY KEY,  -- This sets `student_no` as the primary key
    `name` VARCHAR(50),
    `major` VARCHAR(25)
);
```

### 4.1 Explanation of Table Structure
- **`student_no`**: An integer that serves as the primary key for the table, ensuring uniqueness.
- **`name`**: A variable-length string for the student's name.
- **`major`**: A variable-length string for the student's major field of study.

## 5. Verify Initial Table Structure

To check if your table was created successfully, use the following command:

```sql
DESCRIBE `student`;
```

### 4.2 Expected Output
You should see the following output:

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

### 5.1 Adding a New Column

To add a new column named `score`, use the following command:

```sql
ALTER TABLE `student` ADD `score` INT;
```

#### 5.1.1 Verify Table Structure After Adding Column

Check the updated structure using:

```sql
DESCRIBE `student`;
```

The expected output after adding `score` is as follow:

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

### 5.2 Changing the Data Type

To change the data type of the `score` column to `DECIMAL(3,2)`, use the following command:

```sql
ALTER TABLE `student` MODIFY `score` DECIMAL(3,2);
```

#### 5.2.1 Verify Table Structure After Changing Data Type

Use the command:

```sql
DESCRIBE `student`;
```

The expected output after dropping `score` is as follow:

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

### 5.3 Dropping the Column

To remove the `score` column, use the following command:

```sql
ALTER TABLE `student` DROP `score`;
```

#### 5.3.1 Verify Table Structure After Dropping Column

Check the updated structure using:

```sql
DESCRIBE `student`;
```

The expected output after dropping `score` is as follow:

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

### 5.4 Changing Field Name

To change to field Name from `major` to `field_of_study`, we can use the following command:

```sql
ALTER TABLE `student` CHANGE `major` `field_of_study` VARCHAR(100);
```

#### 5.4.1 Verify Table Structure After Changing Field Name

Check the updated structure using:

```sql
DESCRIBE `student`;
```

The expected output after chaning field name is as follow:

```
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| student_no     | int          | NO   | PRI | NULL    |       |
| name           | varchar(50)  | YES  |     | NULL    |       |
| field_of_study | varchar(100) | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
```


## 6. Dropping the Table

If you need to delete the table `student`, use the following command:

```sql
DROP TABLE `student`;
```

**Caution:** This action is irreversible, and all data within the table will be lost. Ensure you really want to delete `student` before running this command.

## 7. Conclusion

In this section, you learned the essential steps for creating and modifying tables in your MySQL database. We covered the following key points:

- **Table Creation**: You successfully created a table named `student`, defining the appropriate data types for each column.

- **Modifying Tables**: You explored how to add new columns, change data types, and drop columns, allowing for flexibility in managing your table structure.

- **Table Deletion**: You also learned how to permanently delete a table using the `DROP TABLE` command, with a reminder about the irreversible nature of this action.

With these foundational skills, you are now prepared to manage your tables effectively. In the next session, we will focus on **Inserting Data**, where you will learn how to populate your tables with meaningful information.