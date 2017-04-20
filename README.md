# ansible-confluence

An ansible playbook for installing and configuring confluence

Example run: `ansible-playbook -i hosts confluence.yml --ask-vault-pass`

## Assumptions
This playbook is tested on a fresh Ubuntu 14.04 sever install.  Things that may need adapted for other environments include: username (ubuntu), package management (apt), hostsfile (ip).

Ansible Vault is needed to unlock and use the postgress password.  See [Ansible Vault](http://docs.ansible.com/playbooks_vault.html) documentation.

## Actions
This playbook does the following things:
 * update / upgrade apt
 * install postgresql
 * enables postgresql actions (passwordless sudo)
 * creates confluence database and user with appropriate privilege levels
 * installs confluence
 
## TODO
Things we'd like to add
 * service handlers for stop/starting confluence
 * server.xml updater/template
 * backup management  

## Confluence facts
Confluence home is determined by:   
  `/home/ubuntu/atlassian/confluence/confluence/WEB-INF/classes/confluence-init.properties`
Currently, the home directory is set to:  
   `confluence.home = /home/ubuntu/atlassian/application-data/confluence`

### Backup step 1
<img src="confluence backup step 1.jpg" height="200" />

### Backup step 2
<img src="confluence backup step 2.jpg" height="200" />

### Backup step 3
<img src="confluence backup step 3.jpg" height="200" />

### Backup step 4
<img src="confluence backup step 4.jpg" height="200" />

### Backup step 5
<img src="confluence backup step 5.jpg" height="200" />
