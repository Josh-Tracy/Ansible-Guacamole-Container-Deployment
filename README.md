# Ansible-Guacamole-Container-Deployment
Ansible Playbooks to Deploy Guacamole Containers

## Playbooks

### docker_install.yml 
Installs docker. Configured for use with a YUM enabled system. May not work on all systems. 

### deploy_container.yml 
Deploys 3 containers. One for MySQL, one for Apache, and one for Guacamole, and links them together.
* Variables are pulled from /inventory/groupvars/all.yml
* The Guacamole container has a /config directory defined as the GUACAMOLE_HOME environment variable which is linked to /root/opt/guacamole on the host. This is required for using optional modules such as Singl Sign On. 


