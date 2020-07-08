# Ansible-Guacamole-Container-Deployment
Ansible Playbooks to Deploy Guacamole Containers

## Status Of Playbooks on Different Operating Systems

* RHEL 8 - 100% working
* RHEL 7 - 100% Working
* Ubuntu - Work in Progress 

## Prerequisites

* (Optional RHEL8) If you're on a RHEL8 system with no subscription to a repo with Ansible, install the CENTos repo using the following command: yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm 
* (Optional RHEL7) If you're on a RHEL7 system with no subscription to a repo with Ansible, install the EPEL repo using the following command: yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
* Ansible installed. I am using Version 2.9.10
* Define your hosts in the /inventory/hosts file

## Playbooks

### docker_install_rhel7.yml 
Installs docker. Uses yum3 backend vs RHEL8's yum4 backend. Installs container-selinux policies if not available during docker-ce install

### docker_install_rhel8.yml 
Installs docker. Uses yum4 vs RHEL7's yum3 backend. Installs containerd.io dependency for docker-ce install. 

### deploy_container.yml 
Deploys 3 containers. One for MySQL, one for Apache, and one for Guacamole, and links them together.
* Variables are pulled from /inventory/groupvars/all.yml
* The Guacamole container has a /config directory defined as the GUACAMOLE_HOME environment variable which is linked to /root/opt/guacamole on the host. This is required for using optional modules such as Singl Sign On. 

## Instructions
1. Edit the ansible.cfg to mathc your environment. I.E - remote user, ssh key, etc.
2. Edit the /inventory/hosts file to match the host you want to run the playbooks against (--key is optional. Can be defined in ansible.cfg)
Run the playbook for your desired OS: ansible-playbook -i inventory/hosts playbooks/playbook.yml --key=key.pem

