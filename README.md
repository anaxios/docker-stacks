# Docker-Stacks
These are docker-compose files configured to be used behind the included traefik docker-compose.yml setup.

*These are the docker-compose files I personally use. I have tried to make a setup that requires very little fiddling. Please file an issue if something doesn't work. Also feel free to contribute to the list if you are so inclined.*

## Setup

> NOTE: This setup assumes using Cloudflare as a DNS provider and are using origin certs created from the SSL/TLS section of their site.

### SSL Certs

- Put your certs & keys in a safe place. The default is in the `traefik/certs` folder.

Make sure the proper permissions of `600` are set for the certs:
```
sudo chmod 600 <my.crt>
```
- Update the entries in the `config/certs-traefik.yml` to the proper file path and name of your certs.
> NOTE: Don't remove the double quotes from the entries. 

### Create Network

- Create a network named `proxy`. *This is how the containers will network with the Traefik container.*
```
docker network create proxy
```

### Start the Traefik container

- start the traefik container by entering the `traefik` folder and executing:
```
docker-compose up -d
```
## Running a container

*I have tried to make the configuration as automatic as I know how. Most of the cofiguration should be done in the .env files.*

### Setup the `.env`

- Copy the `example.env` file and name it `.env`.

- Read through the `.env` and make changes where appropriate.

Some not so obvious ones maybe be:

`PROJECT_NAME`    <-- **PROBABLY DONT CHANGE THIS**—Traefik will use this to as an identifier</br>
`DOMAIN_NAME`     <-- **VERY IMPORTANT**—Traefik will use this to know which container to route.

### Start the container stack

- Start the containers by executing this in the directory where the `docker-compose.yml` lives:
```
docker-compose up -d
```

---
That should be all there is to it! **PLEASE** raise an issue if something doesn't work.
