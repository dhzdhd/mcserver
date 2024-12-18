# Minecraft Server

## Setup

### Prerequisites

- Download [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html), [Pulumi](https://www.pulumi.com/docs/iac/download-install/), [RClone](https://rclone.org/install/) and [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
- Run `az login` to login to your Microsoft account for Pulumi
- Create an RClone config by executing - `rclone config` and store the `rclone.config` file in the root project directory
- Create a `.env` file using `.env-example` as a template
- Download backups from OneDrive if they exist (only the needed `.tgz` file)

### Local setup

- Copy the preferred backup `.tgz` file to `backups/` directory
- Run `pulumi -C iac/pulumi up -y`
- Run `ansible-playbook --ask-become-pass -i iac/ansible/hosts.yml iac/ansible/playbooks/main.yml`
- Access the server at `<ip_address>:25565`

### Shutdown & Cleanup

- Run `pulumi -C iac/pulumi down -y`

## Configuration

### Server config

- To change server name/VM/location/image..., edit `iac/pulumi/Pulumi.dev.yaml`
- To edit Ansible host config, edit `iac/ansible/hosts.yaml`

### Minecraft config

- To change Minecraft server settings/commands on startup..., edit the environment section in the `mcserver` service in `docker-compose.yml`

## Credit

- [itzg Docker Minecraft server](https://github.com/itzg/docker-minecraft-server)
- [itzg Docker Minecraft backup server](https://github.com/itzg/docker-mc-backup)
