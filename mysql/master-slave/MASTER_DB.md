
### php myadmin 
user : phpmyadmin
pass: xxxxx

CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'xxxxx';
GRANT ALL PRIVILEGES ON * . * TO 'phpmyadmin'@'localhost';

### secure installation
user: root
pass: yyyyy


####
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by "yyyy"


###
mysql -u root -p
password: yyyy


###
goto : sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

bind-address            = 0.0.0.0
server-id               = 1
log_bin                 = /var/log/mysql/mysql-bin.log
binlog_do_db            = myDB 
gtid_mode               = ON
enforce-gtid-consistency= ON
log_slave_updates       = true


### restart mysql
sudo service mysql restart


### 
mysql -u root -p
password: dnj295cvsENjd_JEjC234Bj_nje332BHBW


SHOW DATABASES ;

CREATE DATABASE myDB ;

use myDB ;

CREATE TABLE Persons (
  person_id int,
  name varchar(255)
);

INSERT INTO Persons (person_id, name) VALUES (4, 'Tom');
INSERT INTO Persons (person_id, name) VALUES (2, 'Babu');
INSERT INTO Persons (person_id, name) VALUES (3, 'sub');


### grant replication to all replication



CREATE USER 'repl_slave_1'@'%'  IDENTIFIED WITH mysql_native_password BY 'zzzz' ;

GRANT REPLICATION SLAVE ON *.* TO 'repl_slave_1'@'%' ;

FLUSH PRIVILEGES;


####
** If have to change user password:
ALTER USER 'user'@'%' IDENTIFIED WITH mysql_native_password BY 'zzzz';


###  MASTER STATUS

RESET MASTER;

SHOW MASTER STATUS
+------------------+----------+--------------+------------------+----------------------------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set                      |
+------------------+----------+--------------+------------------+----------------------------------------+
| mysql-bin.000004 |      369 | scobees      |                  | 
+------------------+----------+--------------+------------------+----------------------------------------+


