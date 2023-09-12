@OVERRIDE
(da visualizzare in formato code) 
MySQL Shell 8.0.34

Copyright (c) 2016, 2023, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its affiliates.
Other names may be trademarks of their respective owners.

Type '\help' or '\?' for help; '\quit' to exit.
 MySQL  JS > \sql
Switching to SQL mode... Commands end with ;
 MySQL  SQL > CREATE USER 'developer'@'localhost' IDENTIFIED BY 'passwordhere';
ERROR: Not connected.
 MySQL  SQL > \connect root@localhost
Creating a session to 'root@localhost'
Fetching global names for auto-completion... Press ^C to stop.
Your MySQL connection id is 26 (X protocol)
Server version: 8.0.34 MySQL Community Server - GPL
No default schema selected; type \use <schema> to set one.
 MySQL  localhost:33060+ ssl  SQL > CREATE USER 'developer'@'localhost' IDENTIFIED BY 'passwordhere';
Query OK, 0 rows affected (0.0104 sec)
 MySQL  localhost:33060+ ssl  SQL > FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.0056 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE user 'viewer'@'localhost' IDENTIFIED BY 'passwordhere';
Query OK, 0 rows affected (0.0100 sec)
 MySQL  localhost:33060+ ssl  SQL > FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.0051 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE user 'writer'@'localhost' IDENTIFIED BY 'passwordhere';
Query OK, 0 rows affected (0.0101 sec)
 MySQL  localhost:33060+ ssl  SQL > FLUSH PRIVILEGES
                                 -> ;
Query OK, 0 rows affected (0.0053 sec)
 MySQL  localhost:33060+ ssl  SQL > SELECT User from mysql.user;
+------------------+
| User             |
+------------------+
| developer        |
| mysql.infoschema |
| mysql.session    |
| mysql.sys        |
| root             |
| viewer           |
| writer           |
+------------------+
7 rows in set (0.0005 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE ROLE 'app_developer', 'app_read', 'app_write';
Query OK, 0 rows affected (0.0055 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT ALL ON *.* TO 'app_developer';
Query OK, 0 rows affected (0.0058 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT SELECT ON *.* TO 'app_read';
Query OK, 0 rows affected (0.0048 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT 'app_write' TO 'writer'@'localhost';
Query OK, 0 rows affected (0.0048 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE DATABASE IF NOT EXISTS newdb;
Query OK, 1 row affected (0.0052 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT ALL PRIVILEGES ON newdb . * TO 'developer'@'localhost';
Query OK, 0 rows affected (0.0057 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT SELECT ON newdb.* TO 'viewer'@'localhost';
Query OK, 0 rows affected (0.0035 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT INSERT, UPDATE, DELETE ON newdb.* TO 'writer'@'localhost';
Query OK, 0 rows affected (0.0051 sec)
