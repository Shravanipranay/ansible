Hiw to build docker image for nopCommerce
----------------------------------------

## Manual steps
```
### Installation of docker
* curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```
![preview](images/Screenshot_20230210_114648.png)
```
* sudo usermod -aG docker <username> {username is ubuntu}
 ``` 
![preview](images/Screenshot_20230210_114702.png)
 ```
* exit and relogin
* docker info [This command should not give any errors
```
```
Now clone gthe nopCommerce code from the git.
* git clone https://github.com/nopSolutions/nopCommerce.git
* cd nopCommerce/
* docker image build -t nop:1.0 .
* It will build the docker image
```
![preview](images/Screenshot_20230210_114803.png)



