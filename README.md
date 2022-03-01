# Docker-Stacks
Docker-compose files configured to be used behind the included traefik container.

These are the docker-compose files I personally use. I have tried to make a setup that requires very little fiddling.

### How to use

first create a network named `proxy`. This is where all the containers that have services that need to exposed to the traefik container for proxying live.
```
docker network create proxy
```

start the traefik container by entering the `traefik` folder and executing:
```
docker-compose up -d
```
```
        NOTE that this setup assumes using [cloudflare](https://cloudflare.com/) as a DNS provider and have created origin certs
```
# TODO: finish 
