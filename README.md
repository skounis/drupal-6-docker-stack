# Drupal 6 Docker Stack
PHP 5.3 MySQL 5.6 Containers for Drupal 6

## Containers
MySQL
- https://hub.docker.com/_/mysql

Apache
- https://hub.docker.com/r/iiiepe/apache-drupal6

## Instruction
### Docker

Start the containers 
```
docker pull mysql:5.6
docker pull iiiepe/apache-drupal6
docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.6
docker run -d -v application:/var/www -p 80:80 --name web --link mysql:mysql iiiepe/apache-drupal6
```
### Docker Stack
Use the `docker-compose.yml` 

Start the containers
```
docker-compose up
```

### Access the containers
Login into the container
```
docker exec -it web /bin/bash
```
Access MySQL for the web container
- host: `mysql`
- u: `root`
- p: `root`

```
apt-get update
apt-get install mysql-client
mysql -h mysql -u root -proot
```

### Clean Up
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
