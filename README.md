# Infra template

### Requirements
 * Vagrant (https://www.vagrantup.com/downloads.html)
 * Virtualbox (https://www.virtualbox.org/wiki/Downloads)
 * Ansible (http://docs.ansible.com/ansible/latest/intro_installation.html)

### Setup

**Start VM for the first time**

```
$ git clone git@github.com:silte/infra-template.git folder-name
$ cd THISREPO
```

**Change every 'CHANGE-ME' found**

```
$ grep -r "{CHANGE-ME}" * 
```

**After changing everything**

```
$ ansible-galaxy install -r ansible/requirements.yml -p ansible/roles
$ vagrant up
```

### Configure production server

**Requirements**
 * SSH Access to server as ROOT

**Provision all settings**

```
$ ansible-playbook -i ansible/inventory/production ansible/provision.yml
```
  
**Provision host changes**

 * Go to ``` ansible/group_vars/production.yml ```
 * Follow the instructions

After you've changed your host settings

``` 
$ ansible-playbook -i ansible/inventory/production ansible/provision-apache.yml
```
 
### HOST Configuration


**Add new sites**

 * Create a folder for your site in ``` sites/ ```
 * Go to ``` ansible/group_vars/development.yml ```
 * Follow the instructions

After following the instructions

```
$ vagrant provision
```

**Adding only a new host name**

```
$ ansible-playbook -i ansible/inventory/development ansible/provision-apache.yml
```


**Virtual domain configuration**

```
$ sudo nano /etc/hosts
```

* Add ``` 192.168.55.12 local.local ```
* Open ``` local.local ``` in your browser
 

### Used roles
 
 * [geerlingguy/ansible-role-apache](https://github.com/silte/ansible-role-apache)
 * [geerlingguy/ansible-role-certbot](https://github.com/geerlingguy/ansible-role-certbot)
 * [geerlingguy/ansible-role-composer](https://github.com/geerlingguy/ansible-role-composer)
 * [geerlingguy/ansible-role-drush](https://github.com/geerlingguy/ansible-role-drush)
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
 
