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
````
Create one folder dotnet_roles and then divide the playbook into diffrent yaml files.
create roles and push it into virtual machine by using git hub.
Then run the commnad ansible-playbbok -i hosts filename in virtual machine.
Note: Filename should be in .yaml Format.






