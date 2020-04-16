---
date: 2020-04-14
title: How to enable Performance Schema in MariaDB on CentOS7
categories:
  - databases
description: "How to enable Performance Schema in MariaDB on CentOS7"
type: Document
---

The Performance Schema is a feature for monitoring server performance.

## Prerequisites

- This article is written for non-root users and assumes that you are using a sudo user.
- Installed MariaDB 

## Step 1 - Activating the Performance Schema

Since MariaDB 10.0.12, the performance schema has been disabled by default for performance reasons. You can check its current status by looking at the value of the performance_schema system variable.

The performance schema is disabled by default since MariaDB 10.0.12 for performance reasons. Let's check the status of performance schema.

~~~ bash
SHOW VARIABLES LIKE 'performance_schema';
~~~

~~~ output
+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| performance_schema | OFF   |
+--------------------+-------+
1 row in set (0.001 sec)
~~~

"The performance schema cannot be activated at runtime - it must be set when the server starts by adding the following line in your my.cnf configuration file."

Append the line below under section `mysqld` in file `/etc/my.cnf.d/server.cnf`.

~~~ bash
performance_schema
~~~

Restart the database

~~~ bash
systemctl restart mariadb
~~~

Log in back to the MariaDB database server.

~~~ bash
mysql -u root -p
~~~

Run the command below to see if performance schema is activated

~~~ bash
SHOW VARIABLES LIKE 'performance_schema';
~~~

~~~ bash

~~~ 


## Conclusion
