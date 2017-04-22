# ansible-confluence

An ansible playbook for installing and configuring confluence

Example run: `ansible-playbook confluence.yml --ask-vault-pass`

## Assumptions
This playbook is tested on a fresh Ubuntu 16.04 sever install.

Defaults:
  - username: ubuntu
  - package_mgnt apt
  - hostsfile: hosts
  - database: postgres

Files you need to look at and most likely edit
  - `hosts` - check the IP address matches your desination
  - `confluence.yml`
      - line 8: update the binary to the one used today
      - Line 9: This will change over time, so update it along with line 8
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
Log into confluence as **admin** and click here  
<img src="confluence backup step 1.jpg" height="100" />

### Backup step 2
Scroll down to near the bottom of the screen, and on the left nav bar, click Backup &  Restore  
<img src="confluence backup step 2.jpg" height="100" />

### Backup step 3
Make sure "Back up attachments is checked and click the Back Up button  
<img src="confluence backup step 3.jpg" height="100" />

### Backup step 4
In about 10 to 15 seconds, you will be told where you backup is waiting for you.  
Before you ask, NO, it does not download to your browser!  That would be way to easy.  
<img src="confluence backup step 4.jpg" height="100" />

SCP into the server and grab a copy of that file. Here is a screen shot of the deed being done with winSCP.  
### Backup step 5
<img src="confluence backup step 5.jpg" height="300" />
