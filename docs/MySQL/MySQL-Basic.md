---
sidebar_position: 2
---

# Tables and Keys in MySQL

## 1. Tables

In MySQL, a table is a collection of related data entries organized in rows and columns. Each table has a unique name and consists of various data types.

### Example

The following is an `employees` table:

| **id** | **name**       | **position**   | **hire_date** | **email**                |
|--------|----------------|----------------|----------------|--------------------------|
| 1      | Alice Johnson   | Software Engineer | 2022-01-15     | alice.johnson@example.com |
| 2      | Bob Smith       | Project Manager   | 2021-06-10     | bob.smith@example.com     |
| 3      | Carol Williams   | Data Analyst      | 2023-03-25     | carol.williams@example.com |
| 4      | David Brown     | UX Designer       | 2020-11-08     | david.brown@example.com    |

The following is a `sessions` table:

| **session_id** | **employee_id** | **session_date** | **topic**          |
|-----------------|------------------|------------------|---------------------|
| 1               | 1                | 2023-01-20       | Agile Methodologies  |
| 2               | 2                | 2023-02-15       | Project Management    |
| 3               | 3                | 2023-03-10       | Data Analysis         |
| 4               | 4                | 2023-04-05       | User Experience Design |


## 2. Keys

Keys are used to identify rows in a table and establish relationships between tables.

### 2.1 Primary Key

A primary key is a unique identifier for a record in a table and cannot contain NULL values. For instance, `id` in the `employees` table can serve as the primary key.


### 2.2 Foreign Key

A foreign key is a field in one table that uniquely identifies a row of another table, establishing a relationship between them. 

In our example, the `employee_id` in the `sessions` table is a foreign key that links to the `id` in the `employees` table, allowing you to associate each session with the corresponding employee.

### 2.3 Unique Key

A unique key constraint ensures that all values in a column are different from one another. In our example, the `email` column would have a unique key constraint, ensuring that no two employees can have the same email address.

## 3. Indexes

Indexes are used to speed up the retrieval of rows by creating a data structure that allows fast access to rows. You can create an index on a specific column to improve query performance.
For example, if you frequently query the `employees` table by the `position` column, you can create an index on that column to improve query performance. With the index on the `position` column, queries will directly search `position` but not `id` then `name` then `position` and end the searching.

## Summary

- **Tables**: Organize data in rows and columns.
- **Primary Key**: Unique identifier for records.
- **Foreign Key**: Links two tables together.
- **Unique Key**: Ensures all values in a column are unique.
- **Indexes**: Improve the speed of data retrieval.

The next session will start to introduce the MySQL to generate the above tables