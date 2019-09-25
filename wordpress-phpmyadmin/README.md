2016-04-28:

Docker filesystems are temporary by default.
So we need a volume to presistent data.

Here, we run containers of Wordpress, Mariadb, Phpmyadmin and further Osticket. (Read their doc on hub.docker.com to see what `environment:` their need.)

Run:
# `mkdir db_data && mkdir wordpress` # to hold the db data and wordpress's source code
# `docker-compose up`

(`docker-compose up -d` # run in detach mode
`docker-compose logs` # to see the log)

Reference:
* https://docs.docker.com/engine/userguide/containers/dockervolumes/
* Google: docker wordpress volume storage -> https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04
* https://hub.docker.com/_/wordpress/

--
2016-04-28:
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
--
2016-07-17:
Stackoverflow.com: docker -> How to deal with persistent storage (e.g. databases) in docker (http://stackoverflow.com/questions/18496940/how-to-deal-with-persistent-storage-e-g-databases-in-docker/) - questions about how to deal with persistent storage: by docker volume container, or by folder on local hdd, and which one is better?
--
2019-09-25: 
Update docker-compose file to v3: This file will setup MySQL & PHPMyAdmin with a single command. Add the code below to a file called "docker-compose.yaml" and run the command
This is the original code from https://gist.github.com/bradtraversy/faa8de544c62eef3f31de406982f1d42 (excepts I have changed the ports).

```
$ docker-compose up -d

# To Tear Down
$ docker-compose down --volumes
```

Reference:
Google: docker phpmyadmin -> [Run MySQL & phpMyAdmin locally in 3 steps using Docker](https://medium.com/@migueldoctor/run-mysql-phpmyadmin-locally-in-3-steps-using-docker-74eb735fa1fc)
Google: docker compose phpmyadmin -> [Docker Compose FIle For Wordpress, MySQL & phpmyadmin](https://gist.github.com/bradtraversy/faa8de544c62eef3f31de406982f1d42)

Workon: **"./wordpress-phpmyadmin"** by docker-compose.
