# MySQL

Login:`mysql -u USERNAME -pPASSWORD`

Dump:`mysqldump -u USERNAME -pPASSWORD DATABASENAME > DUMP.SQL`

Restore:`mysql -u USERNAME -pPASSWORD DATABASENAME < DUMP.SQL`

Add user:

```text
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
FLUSH PRIVILEGES;
```

List databases:`SHOW DATABASES;`

Add database:`CREATE DATABASE databasename;`

Use database:`USE databasename;`

Drop database:`DROP DATABASE databasename;`

