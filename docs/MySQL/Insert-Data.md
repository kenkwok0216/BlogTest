---
sidebar_position: 5
---

# Insert Data into the `student` Table

In this section, we will cover how to insert data into the `student` table, which has the following structure:

```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| student_no | int         | NO   | PRI | NULL    |       |
| name       | varchar(50) | YES  |     | NULL    |       |
| major      | varchar(25) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

## 1. Prerequisites

Ensure that you have completed the setup as shown in the session titled [**Creating and Modifying a Table**](/docs/MySQL/Creating-and-Modifying-a-Table).

## 2. Basic Insertion of Data

To insert data into the `student` table, you can use the `INSERT INTO` command. Here are two basic examples:

```sql
INSERT INTO `student` VALUES (1, "Maisie Moran", "Java");
INSERT INTO `student` VALUES (2, "Jemma Roth", NULL);
```

### 2.1 Explanation
- **First Command**: 
  - Inserts a record with `student_no` of `1`, `name` as "Maisie Moran", and `major` as "Java".
  
- **Second Command**: 
  - Inserts a record with `student_no` of `2`, `name` as "Jemma Roth", and `major` as `NULL`.

### 2.2 Verifying Insertion

After executing these commands, verify the inserted data using:

```sql
SELECT * FROM `student`;
```

The expected output will be:

```
+------------+--------------+-------+
| student_no | name         | major |
+------------+--------------+-------+
|          1 | Maisie Moran | Java  |
|          2 | Jemma Roth   | NULL  |
+------------+--------------+-------+
```

## 3. Inserting Data with Specified Columns

You can also specify columns when inserting data. This approach allows you to input values in any order and omit columns that allow NULL values.

### 3.1 Examples

1. **Inserting with Specific Column Order**
   ```sql
   INSERT INTO `student`(`major`, `name`, `student_no`) VALUES ("Physic", "Denzel Hancock", 3);
   ```
   - **Explanation**: Inserts a record specifying `major`, `name`, and `student_no` in a different order.

2. **Inserting with Omitted Column**
   ```sql
   INSERT INTO `student`(`name`, `student_no`) VALUES ("Claire Keller", 4);
   ```
   - **Explanation**: Inserts a record specifying only `name` and `student_no`. The `major` column will default to NULL.

3. **Inserting with NULL Value**
   ```sql
   INSERT INTO `student`(`name`, `major`, `student_no`) VALUES ("Camilla Krueger", NULL, 5);
   ```
   - **Explanation**: Inserts a record with a `NULL` value for `major`, explicitly demonstrating the allowance of NULL values.

### 3.2 Verification After Insertions

After performing these inserts, verify again using:

```sql
SELECT * FROM `student`;
```

You should see:

```
+------------+-----------------+--------+
| student_no | name            | major  |
+------------+-----------------+--------+
|          1 | Maisie Moran    | Java   |
|          2 | Jemma Roth      | NULL   |
|          3 | Denzel Hancock  | Physic |
|          4 | Claire Keller   | NULL   |
|          5 | Camilla Krueger | NULL   |
+------------+-----------------+--------+
```

## 4. Error Handling

When inserting data, you may encounter various types of errors. Here are some common scenarios:

1. **Attempting to Insert Duplicate Primary Key**
   ```sql
   INSERT INTO `student` VALUES (2, "Agnes Harrison", "C");
   ```
   - **Outcome**: This will result in an error:
     ```
     ERROR 1062 (23000): Duplicate entry '2' for key 'student.PRIMARY'
     ```

2. **Type Mismatch Error**
   - If you try to insert a value that doesn't match the expected data type, you'll get an error. For example:
   ```sql
   INSERT INTO `student` VALUES ("three", "Liam Smith", "Maths");
   ```
   - **Outcome**: This will result in an error:
     ```
     ERROR 1366 (22007): Incorrect integer value: 'three' for column 'student_no' at row 1
     ```
   - **Explanation**: Here, the attempt to insert a string ("three") into an integer column (`student_no`) causes a type mismatch error.
   
3. **Column Count Mismatch Error**
   - If the number of columns specified in the `INSERT` statement does not match the number of values provided, you'll encounter an error. For example:
   ```sql
   INSERT INTO `student` (`name`) VALUES ("Ella Oconnell", "Biology);
   ```
   - **Outcome**: This will result in an error:
     ```
     ERROR 1136 (21S01): Column count doesn't match value count at row 1
     ```   
 

## 5. Conclusion

In this section, we explored how to effectively insert data into the `student` table using SQL commands. We covered the basic syntax for inserting records, including specifying values for all columns or only for selected ones. 

Key takeaways include:

- **Data Insertion**: The `INSERT INTO` statement is fundamental for adding records to a table, allowing for flexibility in specifying which columns to fill.

- **Error Handling**: Familiarity with common errors, such as attempting to insert a duplicate primary key, encountering type mismatches, and facing column count mismatches, is vital for effective troubleshooting. Understanding these issues and their implications helps maintain a robust and reliable database.

By mastering these concepts, you can confidently manage data within your MySQL database, ensuring that your applications run smoothly and efficiently. In the next session, we will begin to explore the concept of **constraints** in MySQL. 