How to install nodejs on ubuntu and centos
------------------------------------------
* Ubuntu
### Manual steps
[refer] https://linuxize.com/post/how-to-install-node-js-on-ubuntu-22-04/
```
sudo apt update
sudo apt install nodejs

```
* Centos
 ### Manual steps
 [refer] https://linuxize.com/post/how-to-install-node-js-on-centos-7/
 ```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs

### Ansible Roles
```
Create one folder dotnet_roles and then divide the playbook into diffrent yaml files.
create roles and push it into virtual machine by using git hub.
Then run the commnad ansible-playbbok -i hosts filename in virtual machine.
Note: Filename should be in .yaml Format.
---
 - name: creating roles
   become: yes
   hosts: all
   roles
    - filename
```

### Ansible playbook

By following the manual steps wrote a playbook by using the modules.
And also run it on multidistribution ubuntu and centos
Used nodejs_version as a variable in ansible playbook.
---
- name: install wildfly
  hosts: all
  become: yes
  vars: 
    nodejs_version: 16
  tasks:
    - name: install nodejs using shell file
      shell: "curl -sL https://rpm.nodesource.com/setup_{{ nodejs_version }}.x | sudo bash -"
      when: ansible_facts['distribution'] == 'CentOS' 
    - name: install nodejs
      package:
        name: nodejs
        state: present
        update_cache: yes

