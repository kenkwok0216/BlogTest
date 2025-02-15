---
sidebar_position: 7
---

# Updating and Deleting Data

In this session, we will explore how to **UPDATE** data that has been inserted into the table.

## 1. Prerequisites

Before we begin, please ensure that you have created a database called `sql_tutorial` and have followed the steps in the previous session on [**Constraints**](/docs/MySQL/Constraints).

### 1.1 Checking Your Data

To verify that you have the correct data in your `student` table, run the following SQL command:

```sql
SELECT * FROM `student`;
```

After running the command, the result should look like this:

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

Make sure your data matches the table above before proceeding.

### 1.2 Disable Safe Updates

To make this tutorial doable, we need to disable safe updates with the following command:

```sql
SET SQL_SAFE_UPDATES = 0;
```

## 2. Update Data Examples

### 2.1 Exmaple 1: Updating Major from Maths to Mathematics

Run the following command:

```sql
UPDATE `student` SET `major` = 'Mathematics' WHERE `major` = 'Maths';
```

#### 2.1.1 Explanation

- **UPDATE `student`**: Specifies the table to update.
- **SET `major` = 'Mathematics'**: Changes the `major` column to **Mathematics**.
- **WHERE `major` = 'Maths'**: Filters to update only rows where `major` is **Maths**.

#### 2.1.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+-------------+--------------+
| student_no | name          | major       | religion     |
+------------+---------------+-------------+--------------+
|          1 | Maisie Moran  | Mathematics | Buddhism     |
|          2 | Jemma Roth    | Physics     | Christianity |
|          3 | Claire Kelle  | Biology     | Christianity |
|          4 | Liam Smith    | Chemistry   | No religion  |
|        123 | Alice Johnson | Mathematics | No religion  |
|        124 | Emma Brown    | History     | No religion  |
+------------+---------------+-------------+--------------+
```

**Changes made:**
- The major for **student_no** 1 and **student_no** 123 has changed from **Maths** to **Mathematics**.

### 2.2 Example 2: Changing Religion for a Specific Student

Run the command:

```sql
UPDATE `student` SET `religion` = 'Buddhism' WHERE `student_no` = 124;
```

#### 2.2.1 Explanation

- **UPDATE `student`**: Specifies the table to update.
- **SET `religion` = 'Buddhism'**: Changes the `religion` column to **Buddhism**.
- **WHERE `student_no` = 124**: Ensures that only the row with **student_no** 124 is updated.

#### 2.2.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+-------------+--------------+
| student_no | name          | major       | religion     |
+------------+---------------+-------------+--------------+
|          1 | Maisie Moran  | Mathematics | Buddhism     |
|          2 | Jemma Roth    | Physics     | Christianity |
|          3 | Claire Kelle  | Biology     | Christianity |
|          4 | Liam Smith    | Chemistry   | No religion  |
|        123 | Alice Johnson | Mathematics | No religion  |
|        124 | Emma Brown    | History     | Buddhism     |
+------------+---------------+-------------+--------------+
```

**Changes made:**
- The religion for **student_no** 124 has changed from **No religion** to **Buddhism**.

### 2.3 Example 3: Combining Majors into Biochemistry

Run the command:

```sql
UPDATE `student` SET `major` = 'Biochemistry' WHERE `major` = 'Biology' OR `major` = 'Chemistry';
```

#### 2.3.1 Explanation

- **UPDATE `student`**: Specifies the table to update.
- **SET `major` = 'Biochemistry'**: Changes the `major` column to **Biochemistry**.
- **WHERE `major` = 'Biology' OR `major` = 'Chemistry'**: Updates rows with either **Biology** or **Chemistry**.

#### 2.3.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+--------------+--------------+
| student_no | name          | major        | religion     |
+------------+---------------+--------------+--------------+
|          1 | Maisie Moran  | Mathematics  | Buddhism     |
|          2 | Jemma Roth    | Physics      | Christianity |
|          3 | Claire Kelle  | Biochemistry | Christianity |
|          4 | Liam Smith    | Biochemistry | No religion  |
|        123 | Alice Johnson | Mathematics  | No religion  |
|        124 | Emma Brown    | History      | Buddhism     |
+------------+---------------+--------------+--------------+
```

**Changes made:**
- The major for **student_no** 3 has changed from **Biology** to **Biochemistry**.
- The major for **student_no** 4 has changed from **Chemistry** to **Biochemistry**.

### 2.4 Example 4: Updating Multiple Columns

Run the command:

```sql
UPDATE `student` SET `major` = 'Computer Science', `religion` = 'No religion' WHERE `student_no` = 2;
```

#### 2.4.1 Explanation

- **UPDATE `student`**: Specifies the table for the update.
- **SET `major` = 'Computer Science', `religion` = 'No religion'**: Updates both columns for the specified student.
- **WHERE `student_no` = 2**: Ensures that only the row for student number 2 is updated.

#### 2.4.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+------------------+--------------+
| student_no | name          | major            | religion     |
+------------+---------------+------------------+--------------+
|          1 | Maisie Moran  | Mathematics      | Buddhism     |
|          2 | Jemma Roth    | Computer Science | No religion  |
|          3 | Claire Kelle  | Biochemistry     | Christianity |
|          4 | Liam Smith    | Biochemistry     | No religion  |
|        123 | Alice Johnson | Mathematics      | No religion  |
|        124 | Emma Brown    | History          | Buddhism     |
+------------+---------------+------------------+--------------+
```

**Changes made:**
- The major for **student_no** 2 has changed from **Physics** to **Computer Science**.
- The religion for **student_no** 2 has changed from **Christianity** to **No religion**.

### 2.5 Example 5: Changing a Specific Name

Run the command:

```sql
UPDATE `student` SET `name` = 'Abbie Mccall' WHERE `name` = 'Claire Kelle' AND `religion` = 'Christianity';
```

#### 2.5.1 Explanation

- **UPDATE `student`**: Specifies the table to update.
- **SET `name` = 'Abbie Mccall'**: Changes the value in the `name` column.
- **WHERE `name` = 'Claire Kelle' AND `religion` = 'Christianity'**: Ensures that only the specified record is updated.

#### 2.5.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+------------------+--------------+
| student_no | name          | major            | religion     |
+------------+---------------+------------------+--------------+
|          1 | Maisie Moran  | Mathematics      | Buddhism     |
|          2 | Jemma Roth    | Computer Science | No religion  |
|          3 | Abbie Mccall  | Biochemistry     | Christianity |
|          4 | Liam Smith    | Biochemistry     | No religion  |
|        123 | Alice Johnson | Mathematics      | No religion  |
|        124 | Emma Brown    | History          | Buddhism     |
+------------+---------------+------------------+--------------+
```

**Changes made:**
- The name for **student_no** 3 has changed from **Claire Kelle** to **Abbie Mccall**.

### 2.6 Example 6: Applying a Change to All Rows

Run the command:

```sql
UPDATE `student` SET `religion` = 'No religion';
```

#### 2.6.1 Explanation

- **UPDATE `student`**: Indicates we are updating the `student` table.
- **SET `religion` = 'No religion'**: This command will set the `religion` column to **No religion** for all records.

#### 2.6.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+---------------+------------------+-------------+
| student_no | name          | major            | religion    |
+------------+---------------+------------------+-------------+
|          1 | Maisie Moran  | Mathematics      | No religion |
|          2 | Jemma Roth    | Computer Science | No religion |
|          3 | Abbie Mccall  | Biochemistry     | No religion |
|          4 | Liam Smith    | Biochemistry     | No religion |
|        123 | Alice Johnson | Mathematics      | No religion |
|        124 | Emma Brown    | History          | No religion |
+------------+---------------+------------------+-------------+
```

**Changes made:**
- The religion for all students has changed to **No religion**.

## 3. Conclusion

In this section, we explored how to effectively update data in the `student` table using SQL commands. We covered various scenarios for updating records, including changing specific fields, updating multiple columns, and applying updates broadly.

Key takeaways include:

- **Data Updating**: The `UPDATE` statement is essential for modifying existing records in a table, allowing for precise control over which columns to change and under which conditions.

After talking about `UPDATE`, then we will taking bout `DELETE` in the next session.