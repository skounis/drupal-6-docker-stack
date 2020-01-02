# drupal-6-docker-stack
PHP 5.3 MySQL 5.6 Containers for Drupal 6

## Containers
MySQL
- https://hub.docker.com/_/mysql

Apache
- https://hub.docker.com/r/iiiepe/apache-drupal6

## Instruction

Start the containers 
```
docker pull mysql:5.6
docker pull iiiepe/apache-drupal6
docker run -p 3306:3306 --name mysqlserver -e MYSQL_ROOT_PASSWORD=root -d mysql:5.6
docker run -d -v application:/var/www -p 80:80 --name appserver --link mysqlserver:mysqldb iiiepe/apache-drupal6
```

Login into the container
```
docker exec -it appserver /bin/bash
```

Access MySQL for the web container
```
mysql -h mysqldb -u root -proot
```

Clean Up. Stop and Remove all the container. 
```
docker container stop $(docker container ls -aq)
docker container rm $(docker container ls -aq)
docker system prune --volumes
```

Remove all Image 
```
docker rmi $(docker images -a -q)
```

## References
- Links the Containers
    - https://www.samueledney.com/2016/01/trying-out-docker-php-and-mysql/
- Remove 
    - https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
