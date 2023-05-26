

# Hello !  ʚ♡ɞ
- - - - - - -
### This is a tutorial learn how to use Apache 2 to set up site domain names with Ansible on  Debian 11  VMWARE Workstation Pro.
- -- - - - - 

>Ansible is an open-source automation tool that allows you to automate the provisioning, configuration, and management of systems and applications. It follows a declarative language approach, where you define the desired state of your systems and Ansible takes care of implementing and maintaining that state.

+ We have to make sure you install Ansible on your virtual machine

Run this following code :
```
sudo apt update
sudo apt upgrade

```
  +Install Ansible 
```
sudo apt install Ansible 
```

  + We have to set up the DNS record for the domain names `www.hei.school` ,`front.hei.school`,`back.hei.school` to point to the IP adress on the Debian virtual machine . 
  + New , ve have to create an Ansible playbook which is a list of tasks that automatically execute against hosts, to configure the Apache virtual hosts for the domain names. 
```
Here we will use the script.yaml 
```
  +In the playbook above, we have tp replace debian_servers with the appropriate group name from your inventory file that includes the Debian 11 virtual machine.
  
  + We will create  a directory named templates in the same location as your playbook. In this templates directory, create a template file named `vhost.conf.j2` with the following content:
```
<VirtualHost *:80>
  ServerName {{ inventory_hostname }}
  DocumentRoot /var/www/{{ inventory_hostname }}
</VirtualHost>

```
<sub> This code is in the template file in this repository </sub>

  +Now , we have to run the `ansible-playbook` command :
```
ansible-playbook -i inventory.ini apache_vhosts.yml

```
<sub> Replace inventory.ini with the path of the inventory file.<sub>
  
-----------
### After the playbook completes successfully, the Apache virtual hosts for the domain names will be created and enabled on your Debian 11 virtual machine.
-----------
>  You can now access the websites using the configured domain names in your web browser. 

