# Traefik-Cheating
Traefik Cheating in Writing Configuration Files
- For Using Traefik with Docker, you need to create a network in docker with this cmd `` docker network create --driver=bridge --attachable traefiknet `` or use the default network which the docker-compose creates it for you to use to connect other containers to traefik
- For using with swarm mode use `` --driver=overlay `` instead of `` --driver=bridge ``.

## Traefik Static Configuration with File
- Three modes available for static configurations: ENV Vars, File, CMD Args
- I Love files!
- The following file configures traefik systematically!
- We use dynamic configuration for containers that are intended to connect to traefik
- Inspect the parameters of the file precisely

```bash
################################################################
#
# Configuration sample for Traefik v2.
#
# For Traefik v1: https://github.com/traefik/traefik/blob/v1.7/traefik.sample.toml
#
################################################################

################################################################
# Global configuration
################################################################
global:
  checkNewVersion: true
  sendAnonymousUsage: true

################################################################
# EntryPoints configuration
################################################################

# EntryPoints definition
#
# Optional
#
entryPoints:
  web:
    address: :80

  websecure:
    address: :443

################################################################
# Traefik logs configuration
################################################################

# Traefik logs
# Enabled by default and log to stdout
#
# Optional
#
log:
  # Log level
  #
  # Optional
  # Default: "ERROR"
  #
  level: DEBUG

  # Sets the filepath for the traefik log. If not specified, stdout will be used.
  # Intermediate directories are created if necessary.
  #
  # Optional
  # Default: os.Stdout
  #
  filePath: /etc/traefik/traefik.log

  # Format is either "json" or "common".
  #
  # Optional
  # Default: "common"
  #
#  format: json

################################################################
# Access logs configuration
################################################################

# Enable access logs
# By default it will write to stdout and produce logs in the textual
# Common Log Format (CLF), extended with additional fields.
#
# Optional
#
accessLog:
  # Sets the file path for the access log. If not specified, stdout will be used.
  # Intermediate directories are created if necessary.
  #
  # Optional
  # Default: os.Stdout
  #
  filePath: /etc/traefik/access.log

  # Format is either "json" or "common".
  #
  # Optional
  # Default: "common"
  #
#  format: json

################################################################
# API and dashboard configuration
################################################################

# Enable API and dashboard
#
# Optional
#
api:
  # Enable the API in insecure mode
  #
  # Optional
  # Default: false
  #
  insecure: true

  # Enabled Dashboard
  #
  # Optional
  # Default: true
  #
  dashboard: true

################################################################
# Ping configuration
################################################################

# Enable ping
ping:
  # Name of the related entry point
  #
  # Optional
  # Default: "traefik"
  #
  entryPoint: traefik

################################################################
# Docker configuration backend
################################################################

providers:
  # Enable Docker configuration backend
  docker:
    # Docker server endpoint. Can be a tcp or a unix socket endpoint.
    #
    # Required
    # Default: "unix:///var/run/docker.sock"
    #
    endpoint: unix:///var/run/docker.sock

    # Default host rule.
    #
    # Optional
    # Default: "Host(`{{ normalize .Name }}`)"
    #
    defaultRule: Host(`{{ normalize .Name }}.docker.localhost`)

    # Expose containers by default in traefik
    #
    # Optional
    # Default: true
    #
    exposedByDefault: true
```
