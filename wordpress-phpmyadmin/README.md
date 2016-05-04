Docker filesystems are temporary by default.
So we need a volume to presistent data.

`mkdir db_data && mkdir wordpress` # to hold the db data and wordpress's source code

# docker run --name wordpress -e MYSQL-ROOT_PASSWORD=password -e MYSQL_DATABASE=wordpress -d mariadb

Reference:
Google: docker wordpress volume storage -> https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04
