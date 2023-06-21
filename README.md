# Infrastructure repostiory

Preliminary information on infrastructure:

- IaC based on Ansible tool
- Infrastructure based on containers
- Containers will be managed via docker compose

## Ansible

Ansible tool in this project will be responsible for initializing the server using prepared playbooks:
- ```install_chrome.yml```
- ```install_docker.yml```
- ```configure_project.yml```

### Install Chrome 
This playbook will be responsible for installing Chrome and Chromedriver in Virtual Machine. It will be used to test the program after installation.

### Install Docker 
This playbook will be responsible for installing Docker and Docker Compose in Virtual Machine. Containers will store program modules.

### Configure Project
This playbook is responsible for downloading the project from the production repository and installing it on the server.

## Installation
To install the project you need to:
- In `host_vars` folder add your server. Example: *if your server have address* `192.168.58.4`, *you need to add* `192.168.58.4.yaml` *file*.
- In `inventory/production` file add your server. Example  *if your server have address* `192.168.58.4`, *you need to configure* `docker`, `chrome` *and* `salesman` *section*:
```yaml
[production:children]
docker
salesman

[docker]
192.168.58.4

[chrome]
192.168.58.4

[salesman]
192.168.58.4
```
- Run playbooks:
```bash
ansible-playbook -i inventory/production install_chrome.yml -u root --diff
ansible-playbook -i inventory/production install_docker.yml -u root --diff
ansible-playbook -i inventory/production configure_project.yml -u root --diff
```

