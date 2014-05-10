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

