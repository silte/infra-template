## BEFORE START YOU NEED ##
 * Vagrant (https://www.vagrantup.com/downloads.html)
 * Virtualbox (https://www.virtualbox.org/wiki/Downloads)
 * Ansible (http://docs.ansible.com/ansible/latest/intro_installation.html)








## To start virtual machine first time ##

 1. ``` cd THISREPO ```

 2. ``` grep -r "{CHANGE-ME}" * ``` and change these settings

 3. ``` ansible-galaxy install -r ansible/requirements.yml -p ansible/roles ```

 4. ``` vagrant up ```


## Configure production server ##
  * YOU NEED SSH ACCESS TO SERVER AS ROOT

**Provisio all settings**

* ``` ansible-playbook -i ansible/inventory/production ansible/provision.yml ```
  
  
**Provision (and edit) only host changes**

 * edit ansible/group_vars/production.yml (there are more instructions)

 * ``` ansible-playbook -i ansible/inventory/production ansible/provision-apache.yml ```
 
 
 

## HOST CONFIGURATION ##


**Add new sites**

 * site folder in sites

 * edit ansible/group_vars/development.yml (there are more instructions)

 * ``` vagrant provision ```


 **Adding only a new host name**

 * If only adding a new host name

 * ``` ansible-playbook -i ansible/inventory/development ansible/provision-apache.yml ```


**Virtual domain configuration (local server)**

 * open "sudo nano /etc/hosts"

 * add ``` 192.168.55.12  local.dev ```

 * open "local.dev" in browser
