# cumorah-dockerized

Docker helper for quickly deploying a basic cumorah instance
with template and configuration customizability. This is set up
to fetch SSL certificates automatically using letsencrypt.org.

 * Custom python modules in `dockerdata/python`
 * Custom template overrides in `dockerdata/templates`

### Configurationn options

Configuration options customizable in `.env` file:

 * `CUMORAH_HOSTNAME` **required** hostname for SSL certificate
 * `ACME_CA_SERVER` **required** set to `https://acme-v02.api.letsencrypt.org/directory` to enable SSL certs
 * `LETSENCRYPT_EMAIL` **required** set to email for letsencrypt SSL certificate notifications
 * `DJANGO_SECRET_KEY` **required** Django secret key, see django docs about why this is important
 * `HTTP_LISTEN_PORT` Port to be exposed by docker compose
 * `HTTPS_LISTEN_PORT` Secure port to be exposed by docker compose
 * `CUMORAH_IMAGE` Container image to pull
 * `CUMORAH_TAG` Container image tag to pull
 * `DJANGO_SETTINGS_MODULE` Override settings module to load. Make sure the module exists in dockerdata/python.
 * `DATABASE_URL` Override database connection info instead of using docker compose postgres instance.
   This is useful for configuring a separate managed database instance.

Here is an example .env file

```shell
CUMORAH_HOSTNAME=cumorah.mydomain.com
LETSENCRYPT_EMAIL=itsme@mydomain.com
DJANGO_SECRET_KEY="You really need to come up with a value for this."

# Uncomment to get production certificates once you know you are getting testing certs properly
#ACME_CA_SERVER=https://acme-v02.api.letsencrypt.org/directory

# Get debugging information in traefik logs (proxy service)
#TRAEFIK_LOG_LEVEL=DEBUG
```

### Running Django commands

After starting the container you can use the following commands
to get a shell in the container.

```shell
 # Open bash to run any series of commands on running web container
 docker compose exec -it web /bin/bash

 # Run migrations
 docker compose exec -it web python manage.py migrate 

 # Create a superuser
 docker compose exec -it web python manage.py createsuperuser
```
