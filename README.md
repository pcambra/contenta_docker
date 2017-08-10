```
docker-compose build
docker-compose up
```

# First time initialization of drupal

The container doesn't automatically run `drush site-install` because we want it to be possible to stop and start an existing container without rebuilding the site every time. Instead, you need to manually run this after starting the container the first time:

`docker exec contentadocker_php_1 init-drupal`

In the above command, "contentadocker_php_1" is the name of the running container for the php service. If docker-compose names yours differently, you can find it with `docker-compose ps`.

