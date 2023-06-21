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

### Vagrant

If you don't have a server and would like to run the program locally you can download the Vagrant tool.

- Install Virtualbox
```bash
sudo apt update
sudo apt upgrade
sudo apt install virtualbox
```

- Install Vagrant
```bash
wget https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.deb
sudo apt install ./vagrant_2.2.19_x86_64.deb
```

- Verify Vagrant version
```
vagrant --version
```

- Download `Vagrantfile` from this [repository](https://github.com/Salesman-ai/additional-repository)
- Copy this file to selected folder
- In this folder run command:
```bash
vagrant up
```
- If you want login to VM, run command:
```bash
vagrant ssh
```
**IMPORTANT** Vagrant require your SSH key, so remember to create it for `root` user. Here is [tutoria](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
