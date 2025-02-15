---
sidebar_position: 6
---

# Constraints

In this session, we will introduce the concept of **constraints** in SQL. Constraints are rules that enforce specific conditions on the data in your tables, ensuring data integrity and accuracy.

## 1. Prerequisites

Before we begin, please ensure that you have created a database called `sql_tutorial`. If you already have a `student` table, you will need to remove it before proceeding.

### 1.1 Removing the Existing Table

To remove the existing `student` table, you can execute the following command:

```sql
DROP TABLE `student`;
```

### 1.2 Creating the Student Table with Constraints

After removing the old table, run the following code to create a new `student` table with constraints:

```sql
CREATE TABLE `student` (
    `student_no` INT AUTO_INCREMENT,
    `name` VARCHAR(50) NOT NULL UNIQUE,
    `major` VARCHAR(25) NOT NULL,
    `religion` VARCHAR(50) DEFAULT "No religion",
    PRIMARY KEY(student_no)
);
```

### 1.3 Explanation of Constraints

- **AUTO_INCREMENT**: The `student_no` field will automatically increment with each new record, ensuring unique values.
- **NOT NULL**: The `name` and `major` fields cannot be NULL, meaning every record must have valid values.
- **UNIQUE**: The `name` field must contain unique values, preventing duplicate names for different students.
- **DEFAULT**: The `religion` field will default to "No religion" if no value is provided during insertion.
- **PRIMARY KEY**: The `student_no` field serves as the primary key, uniquely identifying each record in the table.

## 2. Inserting Records

Now that we have created the `student` table, let's insert some records to see how constraints work in practice.

### 2.1 Example 1: Inserting Valid Records

```sql
INSERT INTO `student` (`name`, `major`, `religion`) VALUES ("Maisie Moran", "Maths", "Buddhism");
INSERT INTO `student` (`name`, `major`, `religion`) VALUES ("Jemma Roth", "Physics", "Christianity");
```

- **Explanation**: These commands will successfully insert two records into the `student` table. Both names and majors are valid and unique.

You can run the following command to view the records:

```sql
SELECT * FROM `student`;
```

Expected output:

```
+------------+--------------+---------+--------------+
| student_no | name         | major   | religion     |
+------------+--------------+---------+--------------+
|          1 | Maisie Moran | Maths   | Buddhism     |
|          2 | Jemma Roth   | Physics | Christianity |
+------------+--------------+---------+--------------+
```

### 2.2 Example 2: Insertion with Specified Religion

```sql
INSERT INTO `student` (`name`, `major`, `religion`) VALUES ("Claire Kelle", "Biology", "Christianity");
INSERT INTO `student` (`name`, `major`) VALUES ("Liam Smith", "Chemistry");
```

- **Explanation**: The first command specifies a value for the `religion` field, while the second uses the default value ("No religion") for the `religion` field.

Run the following command to view the updated records:

```sql
SELECT * FROM `student`;
```

Expected output:

```
+------------+--------------+-----------+--------------+
| student_no | name         | major     | religion     |
+------------+--------------+-----------+--------------+
|          1 | Maisie Moran | Maths     | Buddhism     |
|          2 | Jemma Roth   | Physics   | Christianity |
|          3 | Claire Kelle | Biology   | Christianity |
|          4 | Liam Smith   | Chemistry | No religion  |
+------------+--------------+-----------+--------------+
```

### 2.3 Example 3: Valid Insertion with Auto-Increment

```sql
INSERT INTO `student` (`student_no`, `name`, `major`) VALUES (123, "Alice Johnson", "Maths");
INSERT INTO `student` (`name`, `major`) VALUES ("Emma Brown", "History");
```

- **Explanation**: These commands will successfully insert two records into the `student` table. The first command specifies `student_no` explicitly, while the second uses auto-increment for the new record.

Run the following command to view the updated records:

```sql
SELECT * FROM `student`;
```

Expected output:

```
+------------+---------------+-----------+--------------+
| student_no | name          | major     | religion     |
+------------+---------------+-----------+--------------+
|          1 | Maisie Moran  | Maths     | Buddhism     |
|          2 | Jemma Roth    | Physics   | Christianity |
|          3 | Claire Kelle  | Biology   | Christianity |
|          4 | Liam Smith    | Chemistry | No religion  |
|        123 | Alice Johnson | Maths     | No religion  |
|        124 | Emma Brown    | History   | No religion  |
+------------+---------------+-----------+--------------+
```

### 2.4 Example 4: Handling Duplicate Names

```sql
INSERT INTO `student` (`name`, `major`) VALUES ("Liam Smith", "Maths");
```

- **Outcome**: This will result in an error:
  ```
  ERROR 1062 (23000): Duplicate entry 'Liam Smith' for key 'student.name'
  ```
- **Explanation**: The attempt to insert a record with the name "Liam Smith" fails because it already exists, violating the UNIQUE constraint.

### 2.5 Example 5: Insertion with NULL Name

```sql
INSERT INTO `student` (`name`, `major`) VALUES ("Ella Oconnell", NULL);
```

- **Outcome**: This will result in an error:
  ```
  ERROR 1048 (23000): Column 'major' cannot be null
  ```
- **Explanation**: The insertion fails because the `major` field cannot be NULL, as enforced by the NOT NULL constraint.

## 3. Conclusion

In this tutorial, you learned about SQL constraints and their importance in maintaining data integrity within your database. We covered the essential concepts, including:

- **Constraints Overview**: You understood what constraints are and how they enforce rules on data entries.

- **Creating Tables**: You learned how to create a `student` table with various constraints such as `NOT NULL`, `UNIQUE`, and `DEFAULT`.


- **Inserting Records**: You practiced inserting records while respecting constraints and observed outcomes for valid and invalid entries.
- **Error Handling**: You recognized how to handle errors related to constraints, ensuring data validity.

The next session will be **UPDATE** data that has been inserted into the table.
