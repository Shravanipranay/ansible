How to install dotnet on ubuntu and centos
------------------------------------------
* Ubuntu
### Manual steps
```
 [refer] https://linuxhint.com/install_dot_net_core_ubuntu/ 
 sudo apt-get update 
 sudo apt install -y apt-transport-https
 sudo apt install dotnet-sdk-2.2
```
* Centos
### Manual steps
```
[refer] https://linuxhint.com/install_dot_net_core_centos7/
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
sudo /tmp/packages-microsoft-prod.rpm
sudo yum install dotnet-sdk-7.0
```

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
Used version as a variable in ansible playbook.
used when condition when it is required.
---
  - name: install dotnet
    hosts: all
    become: yes
    vars:
      version: 7.0
    tasks:
      - name: install apt transport
        apt:
          name: apt-transport-https
          state: present
          update_cache: yes
        when: ansible_facts['distribution'] == 'Ubuntu'
      - name: install rpm
        get_url:
          url: "https://packages.microsoft.com/config/centos/{{ version }}/packages-microsoft-prod.rpm"
          dest: /tmp/packages-microsoft-prod.rpm
        when: ansible_facts['distribution'] == 'CentOS'
      - name: add pacakge
        yum:
          name: /tmp/packages-microsoft-prod.rpm
          state: present
        when: ansible_facts['distribution'] == 'CentOS' 
      - name: install dotnet
        package:
          name: " dotnet-sdk {{ version }} "
          state: present
          update_cache: yes






