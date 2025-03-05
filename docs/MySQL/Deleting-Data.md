---
sidebar_position: 8
---

# Deleting Data

In this session, we will try to delete data in the database using `DELETE`. The syntax for filtering data is actually the same as that for `UPDATE` data mentioned in the previous session.

## 1. Prerequisites

Before we begin, please ensure that you have created a database called `sql_tutorial` and have followed the steps in the previous session on [**Constraints**](/docs/MySQL/Updating-Data).

### 1.1 Checking Your Data

To verify that you have the correct data in your `student` table, run the following SQL command:

```sql
SELECT * FROM `student`;
```

After running the command, the result should look like this:

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

Make sure your data matches the table above before proceeding.

## 2. Delete Data Examples

**Caution**: Be careful with the `WHERE` clause, omitting it will result in all records being deleted from the table.

### 2.1 Example 1: Simple Deleting Data

Run the following command:

```sql
DELETE FROM `student` WHERE `student_no` = 4;
```

#### 2.1.1 Explanation

- **DELETE FROM `student`**: This command specifies that we want to delete records from the `student` table.
- **WHERE `student_no` = 4**: The `WHERE` clause filters the records to delete only the one where the `student_no` is **4**.

#### 2.1.2 Verification

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
|        123 | Alice Johnson | Mathematics      | No religion |
|        124 | Emma Brown    | History          | No religion |
+------------+---------------+------------------+-------------+
```

**Changes made:**
- `student_no` **4** has been deleted.

### 2.2 Example 2: Delete Numerical Data with Range Specified

Run the following command:

```sql
DELETE FROM `student` WHERE `student_no` > 100;
```

#### 2.2.1 Explanation

- **DELETE FROM `student`**: This command indicates that we want to remove records from the `student` table.
- **WHERE `student_no` > 100**: This condition filters the records to delete all entries where `student_no` is greater than 100.

#### 2.2.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+--------------+------------------+-------------+
| student_no | name         | major            | religion    |
+------------+--------------+------------------+-------------+
|          1 | Maisie Moran | Mathematics      | No religion |
|          2 | Jemma Roth   | Computer Science | No religion |
|          3 | Abbie Mccall | Biochemistry     | No religion |
+------------+--------------+------------------+-------------+
```

**Changes made:**
- Students with `student_no` **123** and **124**, both of which are greater than **100**, have been deleted.

### 2.3 Example 3: Delete Data Containing Specific Characters

Run the following command:

```sql
DELETE FROM `student` WHERE `name` LIKE '%ie%';
```

#### 2.3.1 Explanation

- **DELETE FROM `student`**: This command specifies that we want to delete records from the `student` table.
- **WHERE `name` LIKE '%ie%'**: This condition filters records to delete any entries where the `name` contains the substring "ie".

#### 2.3.2 Verification

After executing:

```sql
SELECT * FROM `student`;
```

This will show you the updated data in the `student` table, as follows:

```
+------------+------------+------------------+-------------+
| student_no | name       | major            | religion    |
+------------+------------+------------------+-------------+
|          2 | Jemma Roth | Computer Science | No religion |
+------------+------------+------------------+-------------+
```

**Changes made:**
- The student with the name **Abbie Mccall** has been deleted, as it contains `ie`.

## 3. Conclusion

In this section, we explored how to effectively delete data from the `student` table using SQL commands. We covered various scenarios for deleting records, including targeting specific entries, deleting in ranges, and removing records based on character patterns.

Key takeaways include:

- **Data Deletion**: The `DELETE` statement is crucial for removing records from a table, with the ability to specify conditions for targeted deletions.

- **Caution**: Be careful with the `WHERE` clause, omitting it will result in all records being deleted from the table.

After talking about `DELETE`, then we will taking about `SELECT` in the next session.