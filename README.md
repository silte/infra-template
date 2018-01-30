## BEFORE START YOU NEED ##
 * Vagrant (https://www.vagrantup.com/downloads.html)
 * Virtualbox (https://www.virtualbox.org/wiki/Downloads)
 * Ansible (http://docs.ansible.com/ansible/latest/intro_installation.html)








## To start virtual machine first time ##

 1.  ``` cd THISREPO ```

 2. ``` ansible-galaxy install -r ansible/requirements.yml -p ansible/roles ```

 3. ``` vagrant up ```




## HOST CONFIGURATION ##


**Add new sites**

 * site folder in sites

 * edit ansible/group_vars/development.yml (there are more instructions)

 * ``` vagrant provision ```


 **Adding only a new host name**

 * If only adding a new host name

 * run ``` ansible-playbook -i ansible/inventory/development ansible/provision-apache.yml ```


**Virtual domain configuration**

 * open "sudo nano /etc/hosts"

 * add ``` 192.168.55.12  local.dev ```

 * open "local.dev" in browser