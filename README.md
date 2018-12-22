# Reverse proxy

## Initialisation

Create an external volume to store the certificates :
```
docker volume create certs
```

Start the container :
```
docker-compose up -d
```

For the first run, get into the certbot container :
```
docker exec -ti certbot bash
```
and generate the certificates with something like :
```
certbot certonly --webroot -w /var/www/letsencrypt --cert-name www.main_domain.com -d www.main_domain.com,main_domain.com,www.other_domain.fr,other_domain.fr,sub1.other_domain.fr,sub2.other_domain.fr
```
then change the path to the certs in snippets/ssl.conf to let Nginx finds them.

## TODO

- Find a way to anonymise the domain name in Nginx's configuration.
