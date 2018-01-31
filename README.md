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
 
## Used roles ##
 
 * [geerlingguy/ansible-role-apache](https://github.com/geerlingguy/ansible-role-apache)
 * [geerlingguy/ansible-role-composer](https://github.com/geerlingguy/ansible-role-composer)
 * [geerlingguy/ansible-role-firewall](https://github.com/geerlingguy/ansible-role-firewall)
 * [geerlingguy/ansible-role-java](https://github.com/geerlingguy/ansible-role-java)
 * [geerlingguy/ansible-role-mailhog](https://github.com/geerlingguy/ansible-role-mailhog)
 * [geerlingguy/ansible-role-mysql](https://github.com/geerlingguy/ansible-role-mysql)
 * [geerlingguy/ansible-role-php](https://github.com/geerlingguy/ansible-role-php)
 * [geerlingguy/ansible-role-php-mysql](https://github.com/geerlingguy/ansible-role-php-mysql)
 * [geerlingguy/ansible-role-php-pecl](https://github.com/geerlingguy/ansible-role-php-pecl)
 * [geerlingguy/ansible-role-php-xdebug](https://github.com/geerlingguy/ansible-role-php-xdebug)
 * [geerlingguy/ansible-role-phpmyadmin](https://github.com/geerlingguy/ansible-role-phpmyadmin)
 * [geerlingguy/ansible-role-postfix](https://github.com/geerlingguy/ansible-role-postfix)
 * [geerlingguy/ansible-role-ruby](https://github.com/geerlingguy/ansible-role-ruby)
 * [idealista/tomcat-role](https://github.com/idealista/tomcat-role)
 
