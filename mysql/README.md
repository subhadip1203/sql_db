### install

### security


### performance
innodb_buffer_pool_size :  can improve performance , generally 124 mb approx

to check , comaand will be  >> SELECT @@innodb_buffer_pool_size;

to change the innodb_buffer_pool_size :

Change file : cd /etc/mysql/my.cnf
  innodb_buffer_pool_size = 2G   
  innodb-buffer-pool-instances=4 