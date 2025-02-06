---
sidebar_position: 1
---

# MySQL Server Installation and Management Tutorial for Linux

## 1. Installing MySQL Server

To install MySQL server on Linux, run:

```bash
sudo apt install mysql-server
```

## 2. Managing MySQL Server Status

### Check Status

To check the status of the MySQL server, use:

```bash
sudo systemctl status mysql
```

### Enable MySQL Server

If the MySQL server is not enabled, run:

```bash
sudo systemctl enable mysql
```

### Disable MySQL Server

To disable the MySQL server, run:

```bash
sudo systemctl disable mysql
```

### Start MySQL Server

To start the MySQL server, use:

```bash
sudo systemctl start mysql
```

### Stop MySQL Server

To stop the MySQL server, run:

```bash
sudo systemctl stop mysql
```

## 3. Securing MySQL Installation

To enhance MySQL server security, execute:

```bash
sudo mysql_secure_installation
```

*Note: This command sets up security rules for the MySQL server.*

## 4. Accessing MySQL Server

To access your MySQL server, run:

```bash
sudo mysql
```

To exit the MySQL server, type:

```sql
exit;
```

## 5. Setting Up Passwords

To set the root password, after logging into MySQL, run:

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
```

To log in with your password, use:

```bash
mysql -u root -p
```

You'll be prompted to enter your password.

## 6. Recovering Forgotten Passwords

If you forget your password, follow these steps:

1. **Stop MySQL Server**:
   ```bash
   sudo service mysql stop
   ```

2. **Start MySQL in Safe Mode**:
   ```bash
   sudo mysqld_safe --skip-grant-tables &
   ```

3. **Log in Without a Password**:
   ```bash
   mysql -uroot
   ```

4. **Update Your Password**:
   ```sql
   FLUSH PRIVILEGES;
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
   exit;
   ```

5. **Restart MySQL Service**:
   ```bash
   sudo service mysql restart
   ```

### Handling Errors

If you encounter the error:

```
"mysqld_safe Directory '/var/run/mysqld' for UNIX socket file doesn't exist."
```

Resolve it by:

a. **Creating the Directory**:
   ```bash
   sudo mkdir -p /var/run/mysqld
   ```

b. **Setting Correct Ownership**:
   ```bash
   sudo chown mysql:mysql /var/run/mysqld
   ```

c. **Setting Correct Permissions**:
   ```bash
   sudo chmod 755 /var/run/mysqld
   ```

d. Return to step 2.

## 7. Accessing MySQL via URL

To access your MySQL server via a web interface, install phpMyAdmin:

```bash
sudo apt install phpmyadmin php
```

### Find Your IP Address

Check your IP address with:

```bash
ip a
```

Get the IP address of `eth0`, for example, `172.10.10.11`. Open your browser and enter:

```
http://172.10.10.11/phpmyadmin/
```

### Handling "NOT FOUND" Error

If you encounter a "NOT FOUND" error, follow these steps:

1. **Create a Symlink**:
   ```bash
   sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
   ```

2. **Enable the Configuration**:
   ```bash
   sudo a2enconf phpmyadmin.conf
   ```

3. **Reload Apache**:
   ```bash
   sudo service apache2 reload
   ```

After these steps, try accessing the URL again, and you should be able to log in to the phpMyAdmin server with your password.

## Conclusion

In this tutorial, you learned how to install and manage MySQL Server on a Linux system. We covered the essential steps, including:

- **Installation**: You successfully installed MySQL Server using the package manager.
- **Service Management**: You learned how to check the server status, enable, disable, start, and stop the MySQL service.
- **Security**: You enhanced the security of your MySQL installation with the `mysql_secure_installation` command and learned how to set and recover passwords.
- **Accessing MySQL**: You accessed the MySQL server and set up root user authentication.
- **Web Interface**: You installed phpMyAdmin for a user-friendly web interface to manage your MySQL databases.

Our next session will start to indroduce some basic concept for Tables and Keys in MySQL.