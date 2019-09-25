## Installation
To run Docker container, we need to install docker-engine.
To run containers in a composition set, we need to install docker-compose.

Installation of them should refer to the offical site of docker: https://docs.docker.com

1. Install Docker Engine (currently v1.12.1)
2. Install Docker Compose (currently v1.8.1)

## Build History

2016-04-25:

Workon: **"./wordpress/"** by docker and docker-compose.

1.
I write a docker-compose.yml file base on these 2 commands:
# docker run --name mariadb -e MYSQL_ROOT_PASSWORD=0858324 -e MYSQL_DATABASE=wordpress -d mariadb
# docker run --name wpdocker --link mariadb:mysql -p 80:80 -d wordpress

To run it, issue `docker-compose up` to run the ./docker-compose.yml

Reference:
* Google Image: docker background -> http://jun.oct-13.us/cn/node/60 -> http://jun.oct-13.us/cn/tags/docker -> http://jun.oct-13.us/cn/article/how-to-use-docker-drupal-create-webform

2.
On how to run wordpress with docker compose,
Google: docker wordpress
* -> https://hub.docker.com/_/wordpress/
* -> http://www.sitepoint.com/how-to-use-the-official-docker-wordpress-image/

3.
On build a wordpress image (with source code) with docker compose,
-> https://docs.docker.com/compose/wordpress/


2016-04-28: 
focus on running Wordpress & MariaDB by docker-compose, rather than running them by issue 2 docker commands.

Workon: **"./wordpress/"** by docker-compose


2016-04-30:
focus on persistent data by volume container, & link a local volume (local folder).

Workon: **"./wordpress-phpmyadmin/" **by docker-compose

2016-10-13:
focus on updating the code of 2016-04-28 that running Wordpress & MariaDB by docker-compose, rather than running them by issue 2 docker commands.
update the code to docker-compose v1.8.1, as the code already written cannot be run.

Workon: **"./wordpress/"** by docker-compose.


2019-03-26:
After learning a lots, I focus on running MySQL + PhpMyAdmin in a rapid way by using docker (instead of using LAMP stack) to support WordPress development.

Workon: **"./WordPress_for_holistic_guidance"** by docker-compose.