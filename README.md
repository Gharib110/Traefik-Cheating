# Traefik-Cheating
Traefik Cheating in Writing Configuration Files
- For Using Traefik with Docker, you need to create a network in docker with this cmd `` docker network create --driver=bridge --attachable traefiknet `` or use the default network which the docker-compose creates it for you to use to connect other containers to traefik
- For using with swarm mode use `` --driver=overlay `` instead of `` --driver=bridge ``.

## Traefik Static Configuration with File
- traefik.yml
- Three modes available for static configurations: ENV Vars, File, CMD Args
- I Love files! So I choose File mode
- The `` traefik.yml `` configures traefik systematically!
- We use dynamic configuration for containers that are intended to connect to traefik
- Inspect the parameters of the file precisely

## Run Traefik
- Traefik supports multiple providers like Nomad, File, Docker, Kubernetes ...
- We use Docker along with Docker Swarm for scaling'
- run its docker-compose file

## Running Whoami Test Containter
- Run `` whoami `` service with `` docker-compose up -d ``
- But before it you should run traefik with docker-compose
- This is just a sample container which helps us to test the traefik well
- Just Run the docker-compose, but before it edit the `` networks  `` section

## User-Defined TLS
- Use the traefik.tls.yml file and put it int othe `` /opt/traefik/dynamic ``. IT is mapped to `` /etc/traefik/dynamic `` in the docker container
- You should use `` docker-compose.tls.whoami.yml `` to enable the tls for it
