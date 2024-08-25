# Jellyfin

[![CI](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml/badge.svg)](https://github.com/DudeCalledBro/jellyfin/actions/workflows/ci.yml)

This repository contains my ansible and docker deployment for Jellyfin - an open-source media server.

## Prerequisites

- Ensure you have Ansible installed (e.g. `pip3 install ansible`)
- Ensure Docker is installed on the Jellyfin server (you may want to checkout my [ansible-docker-role](https://github.com/DudeCalledBro/ansible-role-docker))

## Installation

1. Copy the `example.inventory.yml` file to `inventory.yml` and setup as you need. Ensure you also check the role's defaults.

2. Run the Ansible playbook to deploy Jellyfin

    ```bash
    ansible-playbook play-jellyfin.yml
    ```

> You may have to enter a password to SSH into the target system, so you need to add `-k` after the `ansible-playbook` command.

## License

Copyright © 2024 Niclas Spreng

Licensed under the [MIT license](LICENSE).
