Software name in linux: mysql-server\
Login mysql as root: `mysql -u root -p`

``` sql
Add user
CREATE USER 'finley'@'localhost' 
IDENTIFIED BY 'password'; 
GRANT ALL 
ON *.* 
TO 'mlan'@'localhost' 
WITH GRANT OPTION;
```

Check privileges:\
`Show grants for user@localhost`\
`Show grants for current_user`

List all users:\
`select User from mysql.user`