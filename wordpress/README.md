1.
I write a docker-compose.yml file base on these 2 commands:
# docker run --name mariadb -e MYSQL_ROOT_PASSWORD=0858324 -e MYSQL_DATABASE=wordpress -d mariadb
# docker run --name wpdocker --link mariadb:mysql -p 80:80 -d wordpress

To run it, issue `docker-compose up` (to run the ./docker-compose.yml)

Reference:
* Google Image: docker background -> http://jun.oct-13.us/cn/node/60 -> http://jun.oct-13.us/cn/tags/docker -> http://jun.oct-13.us/cn/article/how-to-use-docker-drupal-create-webform

2.
On how to run wordpress with docker compose,
Google: docker wordpress
* -> https://hub.docker.com/_/wordpress/
* -> http://www.sitepoint.com/how-to-use-the-official-docker-wordpress-image/


