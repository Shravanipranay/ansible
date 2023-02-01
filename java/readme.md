How to install java on ubuntu and centos
------------------------------------------
* Ubuntu
### Manual steps
[refer] https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04
```
sudo apt update
sudo apt install openjdk-11-jdk -y
```
* Centos
 ### Manual steps
 [refer] https://phoenixnap.com/kb/install-java-on-centos
 ```
sudo apt update
sudo apt install java-11-openjdk-devel -y
```
### Ansible Roles
```
Create one folder dotnet_roles and then divide the playbook into diffrent yaml files.
create roles and push it into virtual machine by using git hub.
Then run the commnad ansible-playbbok -i hosts filename in virtual machine.
Note: Filename should be in .yaml Format.
```

### Ansible playbook

By following the manual steps wrote a playbook by using the modules.
And also run it on multidistribution ubuntu and centos
Used version as a variable in ansible playbook.


