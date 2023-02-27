# Sample
- [Hello world](#hello-world)
- [Rabbit](#rabbit)
- [Wordpress with MySQL](#wordpress-with-mysql)

## Hello world
``` bash
docker run hello-world
```

``` bash
docker run hello-world
```

``` bash	
docker ps
```

## Rabbit

https://hub.docker.com/_/rabbitmq

``` bash
 docker run -d rabbitmq:3-management
 ```

``` bash
 docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 rabbitmq:3-management
 ```

``` bash
docker ps
```

http://localhost:8080

``` bash
$ docker run -d --hostname my-rabbit --name some-rabbit -e RABBITMQ_DEFAULT_USER=user -e RABBITMQ_DEFAULT_PASS=password rabbitmq:3-management
```

## Wordpress with MySQL

https://hub.docker.com/_/wordpress/

``` bash
docker run --name some-wordpress -p 8080:80 -d wordpress
```



``` yaml
version: '3.1'

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:
```

``` bash
docker-compose up -d
```

