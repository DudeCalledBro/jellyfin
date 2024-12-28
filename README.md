# Jellyfin

[![CI](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml/badge.svg)](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml)

This repository contains the Ansible code for deploying Jellyfin using Docker.

## Prerequisites

- Ensure you have Ansible installed (e.g. `pip3 install ansible`)
- Ensure Docker is installed on the Jellyfin server (you may want to checkout my [ansible-docker-role](https://github.com/DudeCalledBro/ansible-role-docker))

## Installation

1. Copy the example.inventory.yml file to inventory.yml. You also have to setup a variables file for your configuration. Therefore you have to copy example.config.yml to config.yml. Also have a look into the roles defaults.

> **Important!** You have to provide a tls certificate in order to get the deployment working.

2. Run the Ansible playbook to deploy Jellyfin

    ```bash
    ansible-playbook play-jellyfin.yml
    ```

> You may have to enter a password to SSH into the target system, so you need to add `-k` after the `ansible-playbook` command.

## Watchtower

Watchtower is a Docker container application that automates the process of updating other Docker containers. It monitors running containers and checks for changes to their base images. When Watchtower detects that a new version of an image has been pushed to a Docker registry, it performs the following actions:

- Pulls the updated image
- Gracefully shuts down the existing container
- Restarts the container using the new image with the same runtime options

> **Side Note!** I use Watchtower for effortless updates on my systems, as I often overlook Jellyfin updates. The installation is optional.

```bash
ansible-playbook play-watchtower.yml
```

## License

Copyright © 2024 Niclas Spreng

Licensed under the [MIT license](LICENSE).
