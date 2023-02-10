Write manual steps to build spring pet clinic.
----------------------------------------------

# Manual steps

To install Springpet clinic we need java and also maven for that please follow the below steps.
```
* sudo apt update
* sudo apt install openjdk-17-jdk -y
* java -version
```
![preview](Images/Screenshot_20230209_171600.png)
```
* sudo apt install maven -y
* mvn --version
```
![preview](Images/Screenshot_20230209_171652.png)
* git clone https://github.com/spring-guides/gs-maven.git
* cd gs-maven/initial
* mvn package
```

To see the springpetclic page in the web:
* cd Spring-petclinic
```
![preview](Images/Screenshot_20230209_171850.png)
```
```
* cd target
* java -jar Spring-petclinic-3.0.0-SNAPSHOT.jar
```
```
![preview](Images/Screenshot_20230209_171930.png)
Let's check springpetclinic on web:
http://ip-adress:8080




