---
sidebar_position: 3
---

# MySQL Database: Creation, Verification, and Deletion

To create a new database in MySQL, follow these simple steps:

## 1. **Execute the Create Database Command**

   Use the following SQL command to create a database named `sql_tutorial`:

   ```sql
   CREATE DATABASE `sql_tutorial`;
   ```

   - **Important Notes:**
     - SQL keywords (like `CREATE DATABASE`) are typically written in **uppercase** for better readability.
     - Use **backticks** (`` ` ``) around `sql_tutorial` to handle any special characters or reserved words, ensuring that MySQL interprets it correctly.

## 2. **Verify Database Creation**

   After running the command, check if your database was created successfully by executing:

   ```sql
   SHOW DATABASES;
   ```

   This command will show a list of all databases on your MySQL server. The output will look like this:

   ```
   +--------------------+
   | Database           |
   +--------------------+
   | information_schema |
   | mysql              |
   | performance_schema |
   | phpmyadmin         |
   | sql_tutorial       |
   | sys                |
   +--------------------+
   ```

## 3. **Locate Your Database**

   In the output, look for `sql_tutorial`. If you see it listed, congratulations! Your database has been created successfully.

## 4. **Dropping the Database**

   If you need to delete the database `sql_tutorial`, you can use the following command:

   ```sql
   DROP DATABASE `sql_tutorial`;
   ```

   - **Caution:** This action is irreversible, and all data within the database will be lost. Make sure you really want to delete `sql_tutorial` before running this command.

By following these steps, you can easily set up and manage a new database in MySQL.


## 5. Conclusion

In this tutorial, you learned the essential steps for creating, verifying, and deleting a MySQL database. We covered the following key points:

- **Database Creation**: You successfully created a new database named `sql_tutorial` using the `CREATE DATABASE` command, emphasizing the importance of using SQL keywords in uppercase and backticks for special characters.
  
- **Verification**: You learned how to verify the creation of your database by executing the `SHOW DATABASES` command, allowing you to confirm its presence among other databases on your server.

- **Database Deletion**: You also explored how to delete a database using the `DROP DATABASE` command, with a cautionary reminder about the irreversible nature of this action.

With these foundational skills, you are now prepared to manage your databases effectively. In the next session, we will focus on **Creating and Modifying a Table**.