# cumorah-dockerized

Docker helper for quickly deploying a basic cumorah instance
with template and configuration customizability.

 * Custom python modules in `dockerdata/python`
 * Custom templates in `dockerdata/templates`

Configuration options customizable in `.env` file:

 * `ALLOWED_HOSTS` Comma separated list of domain names: www.mysite.com,otherhost.net 
 * `SECRET_KEY` Django secret key, see django docs about why this is important
 * `LISTEN_PORT` Port to be exposed by docker compose
 * `CUMORAH_IMAGE` Container image to pull
 * `CUMORAH_TAG` Container image tag to pull
 * `DJANGO_SETTINGS_MODULE` Override settings module to load. Make sure this is in dockerdata/python.

After starting the container you can use the following commands
to get a shell in the container.

```shell
 # Open bash to run any series of commands on running web container
 docker exec -it cumorah-dockerized_web_1 /bin/bash

 # Run migrations
 docker exec -it cumorah-dockerized_web_1 python manage.py migrate 

 # Create a superuser
 docker exec -it cumorah-dockerized_web_1 python manage.py createsuperuser
```
