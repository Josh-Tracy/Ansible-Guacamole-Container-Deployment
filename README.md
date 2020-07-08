# Ansible-Guacamole-Container-Deployment
Ansible Playbooks to Deploy Guacamole Containers

## Status Of Playbooks on Different Operating Systems

* RHEL 8 - 100% working
* RHEL 7 - 100% Working
* Ubuntu - Work in Progress 

## Prerequisites

* (Optional) If you're on a RHEL8 system with no subscription to a repo with Ansible, install the CENTos repo using the following command: yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm 
* Ansible installed. I am using Version 2.9.10
* Define your hosts in the /inventory/hosts file

## Playbooks

### docker_install.yml 
Installs docker. Configured for use with a YUM enabled system. May not work on all systems. 

### deploy_container.yml 
Deploys 3 containers. One for MySQL, one for Apache, and one for Guacamole, and links them together.
* Variables are pulled from /inventory/groupvars/all.yml
* The Guacamole container has a /config directory defined as the GUACAMOLE_HOME environment variable which is linked to /root/opt/guacamole on the host. This is required for using optional modules such as Singl Sign On. 


