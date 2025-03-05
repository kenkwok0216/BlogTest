---
sidebar_position: 9
---

# Selecting Data

In this session, we will try to select data in the database using `SELECT`.

## 1. Prerequisites

Before we begin, please ensure that you have created a database called `sql_tutorial` and we will need a new table for this session.

Therefore, run the following command:

```sql
DROP TABLE IF EXISTS `student`;

CREATE TABLE `student` (
    `student_no` INT AUTO_INCREMENT,
    `name` VARCHAR(50) NOT NULL UNIQUE,
    `major` VARCHAR(25) NOT NULL,
    `religion` VARCHAR(50) DEFAULT "No religion",
    `score` INT NOT NULL,
    PRIMARY KEY(student_no)
);

INSERT INTO `student` (`name`, `major`, `religion`, `score`) VALUES
('Alice Smith', 'Biology', 'Christianity', 85),
('Bob Johnson', 'Chemistry', 'No religion', 78),
('Charlie Davis', 'Mathematics', 'Islam', 90),
('Diana Clark', 'Physics', 'Buddhism', 82),
('Ethan Wright', 'Biology', 'Christianity', 88),
('Fiona Harris', 'Chemistry', 'No religion', 45),
('George Lewis', 'Mathematics', 'No religion', 40),
('Hannah Walker', 'Biology', 'Christianity', 91),
('Ian Hall', 'Physics', 'No religion', 76),
('Julia Allen', 'Chemistry', 'Buddhism', 89),
('Kevin Young', 'Mathematics', 'No religion', 35),
('Liam King', 'Biology', 'Christianity', 87),
('Mia Scott', 'Physics', 'Christianity', 92),
('Noah Green', 'Chemistry', 'No religion', 80),
('Olivia Adams', 'Mathematics', 'Buddhism', 30),
('Paul Nelson', 'Biology', 'Christianity', 90),
('Quinn Carter', 'Physics', 'Islam', 85),
('Rachel Mitchell', 'Chemistry', 'No religion', 88),
('Sophie Perez', 'Mathematics', 'Christianity', 91),
('Thomas Roberts', 'Biology', 'Christianity', 77),
('Uma Turner', 'Physics', 'Buddhism', 82),
('Victor White', 'Chemistry', 'Islam', 79),
('Wendy Thompson', 'Mathematics', 'Christianity', 86),
('Xander Martinez', 'Biology', 'No religion', 93),
('Yara Robinson', 'Physics', 'Christianity', 81),
('Zachary Harris', 'Chemistry', 'Buddhism', 84);
```

Then, you will have a table called `student` with 24 entries.

## 2. Select Data Examples

### 2.1 Example 1: Select Integer Data with Ascending Order

Run the following command:

```sql
SELECT * FROM `student` ORDER BY `score`;
```

Then, you will get the following table:

```
+------------+-----------------+-------------+--------------+-------+
| student_no | name            | major       | religion     | score |
+------------+-----------------+-------------+--------------+-------+
|         15 | Olivia Adams    | Mathematics | Buddhism     |    30 |
|         11 | Kevin Young     | Mathematics | No religion  |    35 |
|          7 | George Lewis    | Mathematics | No religion  |    40 |
|          6 | Fiona Harris    | Chemistry   | No religion  |    45 |
|          9 | Ian Hall        | Physics     | No religion  |    76 |
|         20 | Thomas Roberts  | Biology     | Christianity |    77 |
|          2 | Bob Johnson     | Chemistry   | No religion  |    78 |
|         22 | Victor White    | Chemistry   | Islam        |    79 |
|         14 | Noah Green      | Chemistry   | No religion  |    80 |
|         25 | Yara Robinson   | Physics     | Christianity |    81 |
|         21 | Uma Turner      | Physics     | Buddhism     |    82 |
|          4 | Diana Clark     | Physics     | Buddhism     |    82 |
|         26 | Zachary Harris  | Chemistry   | Buddhism     |    84 |
|          1 | Alice Smith     | Biology     | Christianity |    85 |
|         17 | Quinn Carter    | Physics     | Islam        |    85 |
|         23 | Wendy Thompson  | Mathematics | Christianity |    86 |
|         12 | Liam King       | Biology     | Christianity |    87 |
|         18 | Rachel Mitchell | Chemistry   | No religion  |    88 |
|          5 | Ethan Wright    | Biology     | Christianity |    88 |
|         10 | Julia Allen     | Chemistry   | Buddhism     |    89 |
|         16 | Paul Nelson     | Biology     | Christianity |    90 |
|          3 | Charlie Davis   | Mathematics | Islam        |    90 |
|         19 | Sophie Perez    | Mathematics | Christianity |    91 |
|          8 | Hannah Walker   | Biology     | Christianity |    91 |
|         13 | Mia Scott       | Physics     | Christianity |    92 |
|         24 | Xander Martinez | Biology     | No religion  |    93 |
+------------+-----------------+-------------+--------------+-------+
```

Then, you will get the table sorted by score in ascending order.

#### 2.1.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **ORDER BY `score`**: This clause sorts the results by the `score` column in ascending order.

### 2.2 Example 2: Select Integer Data with Descending Order

Run the following command:

```sql
SELECT * FROM `student` ORDER BY `score` DESC;
```

Then, you will get the following table:

```
+------------+-----------------+-------------+--------------+-------+
| student_no | name            | major       | religion     | score |
+------------+-----------------+-------------+--------------+-------+
|         24 | Xander Martinez | Biology     | No religion  |    93 |
|         13 | Mia Scott       | Physics     | Christianity |    92 |
|         19 | Sophie Perez    | Mathematics | Christianity |    91 |
|          8 | Hannah Walker   | Biology     | Christianity |    91 |
|         16 | Paul Nelson     | Biology     | Christianity |    90 |
|          3 | Charlie Davis   | Mathematics | Islam        |    90 |
|         10 | Julia Allen     | Chemistry   | Buddhism     |    89 |
|         18 | Rachel Mitchell | Chemistry   | No religion  |    88 |
|          5 | Ethan Wright    | Biology     | Christianity |    88 |
|         12 | Liam King       | Biology     | Christianity |    87 |
|         23 | Wendy Thompson  | Mathematics | Christianity |    86 |
|          1 | Alice Smith     | Biology     | Christianity |    85 |
|         17 | Quinn Carter    | Physics     | Islam        |    85 |
|         26 | Zachary Harris  | Chemistry   | Buddhism     |    84 |
|         21 | Uma Turner      | Physics     | Buddhism     |    82 |
|          4 | Diana Clark     | Physics     | Buddhism     |    82 |
|         25 | Yara Robinson   | Physics     | Christianity |    81 |
|         14 | Noah Green      | Chemistry   | No religion  |    80 |
|         22 | Victor White    | Chemistry   | Islam        |    79 |
|          2 | Bob Johnson     | Chemistry   | No religion  |    78 |
|         20 | Thomas Roberts  | Biology     | Christianity |    77 |
|          9 | Ian Hall        | Physics     | No religion  |    76 |
|          6 | Fiona Harris    | Chemistry   | No religion  |    45 |
|          7 | George Lewis    | Mathematics | No religion  |    40 |
|         11 | Kevin Young     | Mathematics | No religion  |    35 |
|         15 | Olivia Adams    | Mathematics | Buddhism     |    30 |
+------------+-----------------+-------------+--------------+-------+
```

Then, you will get the table sorted by `score` in descending order.

#### 2.2.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **ORDER BY `score` DESC**: This clause sorts the results by the `score` column in descending order.

### 2.3 Example 3: Select Multiple Integer Data with Order

Run the following command:

```sql
SELECT * FROM `student` ORDER BY `score` DESC, `student_no` ASC;
```

Then, you will get the following table:

```
+------------+-----------------+-------------+--------------+-------+
| student_no | name            | major       | religion     | score |
+------------+-----------------+-------------+--------------+-------+
|         24 | Xander Martinez | Biology     | No religion  |    93 |
|         13 | Mia Scott       | Physics     | Christianity |    92 |
|          8 | Hannah Walker   | Biology     | Christianity |    91 |
|         19 | Sophie Perez    | Mathematics | Christianity |    91 |
|          3 | Charlie Davis   | Mathematics | Islam        |    90 |
|         16 | Paul Nelson     | Biology     | Christianity |    90 |
|         10 | Julia Allen     | Chemistry   | Buddhism     |    89 |
|          5 | Ethan Wright    | Biology     | Christianity |    88 |
|         18 | Rachel Mitchell | Chemistry   | No religion  |    88 |
|         12 | Liam King       | Biology     | Christianity |    87 |
|         23 | Wendy Thompson  | Mathematics | Christianity |    86 |
|          1 | Alice Smith     | Biology     | Christianity |    85 |
|         17 | Quinn Carter    | Physics     | Islam        |    85 |
|         26 | Zachary Harris  | Chemistry   | Buddhism     |    84 |
|          4 | Diana Clark     | Physics     | Buddhism     |    82 |
|         21 | Uma Turner      | Physics     | Buddhism     |    82 |
|         25 | Yara Robinson   | Physics     | Christianity |    81 |
|         14 | Noah Green      | Chemistry   | No religion  |    80 |
|         22 | Victor White    | Chemistry   | Islam        |    79 |
|          2 | Bob Johnson     | Chemistry   | No religion  |    78 |
|         20 | Thomas Roberts  | Biology     | Christianity |    77 |
|          9 | Ian Hall        | Physics     | No religion  |    76 |
|          6 | Fiona Harris    | Chemistry   | No religion  |    45 |
|          7 | George Lewis    | Mathematics | No religion  |    40 |
|         11 | Kevin Young     | Mathematics | No religion  |    35 |
|         15 | Olivia Adams    | Mathematics | Buddhism     |    30 |
+------------+-----------------+-------------+--------------+-------+
```

Then, you will get the table sorted by `score` in descending order and `student_no` in ascending order. Note that `ASC` is not required since it is the default.

#### 2.3.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **ORDER BY `score` DESC, `student_no` ASC**: This clause sorts the results first by the `score` column in descending order and then by the `student_no` column in ascending order.

### 2.4 Example 4: Selec a Limited Number of Data

Provided that you do not want to print out all data, say you only need **3** entries.

Run the following command:

```sql
SELECT * FROM `student` LIMIT 3;
```

Then, you will get the following table:

```
+------------+---------------+-------------+--------------+-------+
| student_no | name          | major       | religion     | score |
+------------+---------------+-------------+--------------+-------+
|          1 | Alice Smith   | Biology     | Christianity |    85 |
|          2 | Bob Johnson   | Chemistry   | No religion  |    78 |
|          3 | Charlie Davis | Mathematics | Islam        |    90 |
+------------+---------------+-------------+--------------+-------+
```

Then, you will get only the top **3** entries from the `student` table.

#### 2.4.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **LIMIT 3**: This clause restricts the number of rows returned by the query to **3**.

### 2.5 Example 5: Select Top N Students

With the syntax in Example 4, we can print out the top **5** students by score.

Run the following command:

```sql
SELECT * FROM `student` ORDER BY `score` DESC LIMIT 5;
```

Then, you will get the following table:

```
+------------+-----------------+-------------+--------------+-------+
| student_no | name            | major       | religion     | score |
+------------+-----------------+-------------+--------------+-------+
|         24 | Xander Martinez | Biology     | No religion  |    93 |
|         13 | Mia Scott       | Physics     | Christianity |    92 |
|         19 | Sophie Perez    | Mathematics | Christianity |    91 |
|          8 | Hannah Walker   | Biology     | Christianity |    91 |
|          3 | Charlie Davis   | Mathematics | Islam        |    90 |
+------------+-----------------+-------------+--------------+-------+
```

Then, you will get the top **5** students sorted by score in descending order.

#### 2.5.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **ORDER BY `score` DESC**: This clause sorts the results by the `score` column in descending order.
- **LIMIT 5**: This clause restricts the number of rows returned by the query to the top **5**.

### 2.6 Example 6: Select Data Using `IN()`

Run the following command:

```sql
SELECT * FROM `student` WHERE `major` IN("Biology", "Mathematics");
```

Then, you will get the following table:

```
+------------+-----------------+-------------+--------------+-------+
| student_no | name            | major       | religion     | score |
+------------+-----------------+-------------+--------------+-------+
|          1 | Alice Smith     | Biology     | Christianity |    85 |
|          3 | Charlie Davis   | Mathematics | Islam        |    90 |
|          5 | Ethan Wright    | Biology     | Christianity |    88 |
|          7 | George Lewis    | Mathematics | No religion  |    40 |
|          8 | Hannah Walker   | Biology     | Christianity |    91 |
|         11 | Kevin Young     | Mathematics | No religion  |    35 |
|         12 | Liam King       | Biology     | Christianity |    87 |
|         15 | Olivia Adams    | Mathematics | Buddhism     |    30 |
|         16 | Paul Nelson     | Biology     | Christianity |    90 |
|         19 | Sophie Perez    | Mathematics | Christianity |    91 |
|         20 | Thomas Roberts  | Biology     | Christianity |    77 |
|         23 | Wendy Thompson  | Mathematics | Christianity |    86 |
|         24 | Xander Martinez | Biology     | No religion  |    93 |
+------------+-----------------+-------------+--------------+-------+
```

Then, you will get all entries where the major is either "Biology" or "Mathematics".

#### 2.6.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **WHERE `major` IN("Biology", "Mathematics")**: This condition filters the records to include only those where the `major` is either "Biology" or "Mathematics".

### 2.7 Example 7: Combined Query

Run the following command to combine the previous examples:

```sql
SELECT * FROM `student` WHERE `major` = "Biology" ORDER BY `score` DESC LIMIT 3;
```

Then, you will get the following table:

```
+------------+-----------------+---------+--------------+-------+
| student_no | name            | major   | religion     | score |
+------------+-----------------+---------+--------------+-------+
|         24 | Xander Martinez | Biology | No religion  |    93 |
|          8 | Hannah Walker   | Biology | Christianity |    91 |
|         16 | Paul Nelson     | Biology | Christianity |    90 |
+------------+-----------------+---------+--------------+-------+
```

Then, you will get the top **3** students who are majoring in "Biology," sorted by score in descending order.

#### 2.7.1 Explanation

- **SELECT * FROM `student`**: This command retrieves all columns from the `student` table.
- **WHERE `major` = "Biology"**: This condition filters the records to include only those where the `major` is "Biology".
- **ORDER BY `score` DESC**: This clause sorts the results by the `score` column in descending order.
- **LIMIT 3**: This clause restricts the number of rows returned by the query to **3**.

## 3. Conclusion

In this section, we explored how to effectively select data from the `student` table using SQL commands. We covered various scenarios for retrieving records, including sorting data, limiting results, and filtering based on specific criteria.

Key takeaways include:

- **Data Selection**: The `SELECT` statement is crucial for retrieving data from a table, allowing for control over which columns to display and under what conditions.
- **Sorting and Filtering**: Utilizing `ORDER BY` and `WHERE` clauses enables precise control over the order and relevance of the data retrieved.
- **Limiting Results**: The `LIMIT` clause is useful for restricting the number of rows returned, which is particularly helpful for summarizing large datasets.
- **Using `IN()` for Conditions**: The `IN()` function simplifies queries that involve multiple conditions, making SQL statements cleaner and easier to read.
