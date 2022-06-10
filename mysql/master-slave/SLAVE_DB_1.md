


### slave 1 Mysql
ssh -i "keyr" root@ip



### php myadmin 
user : phpmyadmin
pass: xxx

CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'xxx';
GRANT ALL PRIVILEGES ON * . * TO 'phpmyadmin'@'localhost';



####
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by "yyy"
FLUSH PRIVILEGES;


### secure installation
sudo mysql_secure_installation
user: root
pass: yyy

###
mysql -u root -p
password: yyy




### mysql >

SHOW DATABASES ;

CREATE DATABASE scobees ;

use scobees ;

CREATE TABLE Persons (
  person_id int,
  name varchar(255)
);


###
goto : sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

bind-address            = 0.0.0.0
server-id               = 2
log_bin                 = /var/log/mysql/mysql-bin.log
binlog_do_db            = scobees                 
relay_log               = /var/log/mysql/mysql-relay.log
gtid_mode               = ON
enforce-gtid-consistency= ON

### restart mysql
sudo service mysql restart



### add master

STOP SLAVE ;
RESET SLAVE;
CHANGE MASTER TO  MASTER_HOST= 'ip.address.master.server' , 
                  MASTER_USER = 'repl_slave_1' ,
                  MASTER_PASSWORD = 'yyy' , 
                  MASTER_LOG_FILE = 'mysql-bin.000001' , 
                  MASTER_LOG_POS = 4578 ;

START SLAVE ;

SHOW SLAVE STATUS\G ;

