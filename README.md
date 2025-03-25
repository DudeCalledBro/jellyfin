# Jellyfin

[![CI](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml/badge.svg)](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml)

This repository contains the Ansible code for deploying Jellyfin using Docker.

## Prerequisites

- Ensure you have Ansible installed (e.g. `pip3 install ansible`)
- Ensure Docker is installed on the Jellyfin server (you may want to checkout my [ansible-docker-role](https://github.com/DudeCalledBro/ansible-role-docker))
- **Optional**: Set up a reverse proxy for your Jellyfin instance (you may want to checkout my [traefik-deployment](https://github.com/DudeCalledBro/traefik-ansible))

## Installation

1. Copy the example.inventory.yml file to inventory.yml. You also have to setup a variables file for your configuration. Therefore you have to copy example.config.yml to config.yml.

2. Configure the setup (config.yml), such as the Traefik reverse proxy.

    ```yaml
    # Docker Compose override configuration for Jellyfin container
    jellyfin_docker_override:
      services:
        jellyfin:
          labels:
            - traefik.enable=true
            - traefik.http.routers.jellyfin.rule=Host(`jellyfin.local`)
            - traefik.http.routers.jellyfin.entrypoints=websecure
            - traefik.http.routers.jellyfin.tls=true
            - traefik.http.services.jellyfin.loadBalancer.server.port=8096
          networks:
            - traefik
    
      # Custom networking in your docker compose override
      networks:
        traefik:
          name: traefik
    ```

3. Run the Ansible playbook to deploy Jellyfin

    ```bash
    ansible-playbook main.yml
    ```

> You may have to enter a password to SSH into the target system, so you need to add `-k` after the `ansible-playbook` command.

## License

Copyright © 2024 Niclas Spreng

Licensed under the [MIT license](LICENSE).
