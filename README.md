# Traefik-Cheating
Traefik Cheating in Writing Configuration Files
- For Using Traefik with Docker, you need to create a network in docker with this cmd `` docker network create --driver=bridge --attachable traefiknet `` or use the default network which the docker-compose creates it for you to use to connect other containers to traefik
- For using with swarm mode use `` --driver=overlay `` instead of `` --driver=bridge ``.

## Traefik Static Configuration with File
- traefik.yml
- Three modes available for static configurations: ENV Vars, File, CMD Args
- I Love files!
- The following file configures traefik systematically!
- We use dynamic configuration for containers that are intended to connect to traefik
- Inspect the parameters of the file precisely

## Running Whoami Test Containter
- Run `` whoami `` service with `` docker-compose up -d ``
- But before it you should run traefik with docker-compose
