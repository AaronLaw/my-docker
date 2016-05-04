2016-04-28:

Docker filesystems are temporary by default.
So we need a volume to presistent data.

Run:
# `mkdir db_data && mkdir wordpress` # to hold the db data and wordpress's source code
# `docker-compose up`

(`docker-compose up -d` # run in detach mode
`docker-compose logs` # to see the log)

Reference:
Google: docker wordpress volume storage -> https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04

--

Docker filesystems are temporary by default. #  (https://www.digitalocean.com/community/tutorials/how-to-work-with-docker-data-volumes-on-ubuntu-14-04)
The data in db is not persistent after `docker rm wordpressdb`.
So, we need a volume, which can be a volume or a volume container, to persistent data (data will not be lost after stopping the db container)

(Ref:
https://docs.docker.com/engine/userguide/containers/dockervolumes/, or see https://hub.docker.com/_/mariadb/
Google: docker wordpress volume storage -> https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04 -> https://www.digitalocean.com/community/tutorials/how-to-work-with-docker-data-volumes-on-ubuntu-14-04 & https://www.digitalocean.com/community/tutorials/how-to-work-with-docker-data-volumes-on-ubuntu-14-04
)

`docker run --name wordpressdb_vol -v $(pwd):/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=wordpress -d mariadb` # How do I know the default path fo mysql? `docker inspect wordpressdb` and look for the Mount pont
`docker logs wordpressdb_vol` # to see if there errors
`docker run --name wpdocker --link wordpressdb_vol:mysql -p 80:80 -d wordpress:latest`

After stop & rm both the wordpressdb_vol and wpdocker, and re-run them again, I can see the db data is kept in the pwd.
