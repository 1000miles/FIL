# MySQL Basics - Part I

In the first part you will learn the basics of sql commands: SHOW, USE, SELECT, LIMIT & ORDER BY. For a better readability by convention the commands are used in all capitals even though they would also work in lower case. You need to use `;` at the end of each code block to let MySQL know that it has ended. A sql code block can contain one or multiple statements. Each command you execute to return a value is a statement.

**To log into the mysql server (where no credentials are required, e.g. development environment) do:**
`mysql -u root;`

**To show all databases do:**
`SHOW databases;`

Output:
```
+-----------------------+
| Database              |
+-----------------------+
| information_schema    |
| mysql                 |
| performance_schema    |
| sys              |
| project_development   |
| project_test          |
+-----------------------+
6 rows in set (0.00 sec)
```

**To change into one of the databases do:**
`USE project_development;`

**To display all tables do:**
`SHOW tables;`

Output:
```
+--------------------------------+
| Tables_in_project_development  |
+--------------------------------+
| countries                      |
| cities                         |
| regions                        |
| categories                     |
| tags                           |
| roles                          |
| users                          |
| photos                         |                
| schema_migrations              |
| slugs                          |
+--------------------------------+
10 rows in set (0.00 sec)
```

**To select all from the table `categories` in the tables list `Tables_in_project_development` do:**
`SELECT * FROM categories;`

**To select all from the table `categories` in the tables list `Tables_in_project_development` and limit it to 7 entries do:**
`SELECT * FROM categories LIMIT 7;`

Output:
```
+----+-----------------+---------------------+---------------------+
| id | identifier      | created_at          | updated_at          |
+----+-----------------+---------------------+---------------------+
|  1 | transport       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  2 | food            | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  3 | leisure         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  4 | education       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  5 | shopping        | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  6 | sport           | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  7 | tourism         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
+----+-----------------+---------------------+---------------------+
7 rows in set (0.00 sec)
```

Note: By default entries are ordered by ID in an ascending order unless you specify the order category.

**To order the entries by the first column (in this case it's ID) do:**
```
SELECT * FROM categories
LIMIT 7
ORDER BY 1; (or: ORDER BY id)
```
Output:
```
+----+-----------------+---------------------+---------------------+
| id | identifier      | created_at          | updated_at          |
+----+-----------------+---------------------+---------------------+
|  1 | transport       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  2 | food            | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  3 | leisure         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  4 | education       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  5 | shopping        | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  6 | sport           | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  7 | tourism         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
+----+-----------------+---------------------+---------------------+
7 rows in set (0.00 sec)
```
As you may see there is no difference to the default order behavior above.

**To order the entries by the second column (in this case it's identifier, a-z) do:**
```
SELECT * FROM categories
LIMIT 7
ORDER BY 2; (or: ORDER BY identifier)
```
Output:
```
+----+-----------------+---------------------+---------------------+
| id | identifier      | created_at          | updated_at          |
+----+-----------------+---------------------+---------------------+
|  4 | education       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  2 | food            | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  3 | leisure         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  5 | shopping        | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  6 | sport           | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  7 | tourism         | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
|  1 | transport       | 2016-01-09 00:06:06 | 2016-01-09 00:06:06 |
+----+-----------------+---------------------+---------------------+
7 rows in set (0.00 sec)
```
