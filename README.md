# drupal-6-docker-stack
PHP 5.3 MySQL 5.6 Containers for Drupal 6

Start the containers 
```
docker pull mysql/mysql-server:5.6
docker pull iiiepe/apache-drupal6
docker run -p 3306:3306 --name mysqlserver -e MYSQL_ROOT_PASSWORD=root -d mysql/mysql-server:5.6
docker run -d -v application:/var/www -p 80:80 --name appserver --link mysqlserver:mysqldb iiiepe/apache-drupal6
```

## Containers
MySQL
- https://hub.docker.com/_/mysql

Apache
- https://hub.docker.com/r/iiiepe/apache-drupal6

## Instruction

## References
- Links the Containers
    - https://www.samueledney.com/2016/01/trying-out-docker-php-and-mysql/
