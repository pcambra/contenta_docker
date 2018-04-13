# Getting started

The following instructions will build the master 8.x-1.x build of the ContentaCMS and run in your active shell
```
docker-compose build
docker-compose up
```

This set of instructions will build according to a particular branch or tag of the ContentaCMS and run your containers detached (great if you have another application that monitors active containers (i.e.: kitematic)
```
docker-compose build --build-arg CMS_VERSION=v1.477
docker-compose up -d
```

# First-time initialization

The container doesn't automatically run `drush site-install` because we want it to be possible to stop and start an existing container without rebuilding the site every time. Instead, you need to manually run this after starting the container the first time:

`docker exec contentadocker_php_1 init-drupal`

_In the above command, "contentadocker_php_1" is the name of the running container for the php service. If docker-compose names yours differently, you can find it with `docker-compose ps`._

When it finishes successsfully, the command will output a one-time login URL.

# Persistence

Persistent state is stored in two docker volumes (named `data` and `www`). You can destroy and recreate the containers as much as you like and your site will be preserved until you also destroy these volumes.

# .env File

You'll note that you can manage to change up some of the core values for the default db build configuration as well as where the services will sit and what ports they use externally. 


```
MYSQL_DATABASE=contenta
MYSQL_USER=contenta
MYSQL_PASSWORD=contenta
MYSQL_ALLOW_EMPTY_PASSWORD=yes
MYSQL_ROOT_PASSWORD=root

HOSTNAME=contenta.local
HOSTIP=192.168.1.1

HOST_MYSQL_PORT=3336
HOST_PHP_PORT=9009
HOST_HTTP_PORT=8888
HOST_HTTPS_PORT=8443
```

It's really important to manage these values according to where this solution will sit. Both in a secure and insecure environment.
