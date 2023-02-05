Manual steps for Tomcat.
-------------------------

* sudo apt update

* sudo apt install openjdk-11-jdk
* sudo groupadd tomcat
* sudo useradd tomcat -s /bin/false -d /opt/tomcat
* sudo wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.0.8/bin/apache-tomcat-10.0.8.tar.gz

* sudo tar zxvf apache-tomcat-10.0.8.tar.gz
* sudo chown -r tomcat:tomcat /opt/tomcat
* sudo chmod +x /opt/tomcat/latest/bin/*.sh
* sudo vi /etc/systemd/system/tomcat.service
```
[Unit]

Description=Tomcat

After=network.target



[Service]

Type=forking



User=root

Group=root



Environment="JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64"

Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"

Environment="CATALINA_BASE=/opt/tomcat"

Environment="CATALINA_HOME=/opt/tomcat"

Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"

Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"



ExecStart=/opt/tomcat/bin/startup.sh

ExecStop=/opt/tomcat/bin/shutdown.sh



[Install]

WantedBy=multi-user.target
```
* sudo systemctl daemon-reload 
* sudo nano /opt/tomcat/conf/tomcat-users.xml
```
<!-- user manager can access only manager section -->

<role rolename="manager-gui" />

<user username="manager" password="StrongPassword" roles="manager-gui" />



<!-- user admin can access manager and admin section both -->

<role rolename="admin-gui" />

<user username="admin" password="StrongPassword" roles="manager-gui,admin-gui" />
```
* sudo nano /opt/tomcat/webapps/manager/META-INF/context.xml
```
<!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"

         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
```
* sudo nano /opt/tomcat/webapps/host-manager/META-INF/context.xml
```
<!--<Valve className="org.apache.catalina.valves.RemoteAddrValve"

         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
```
* sudo systemctl restart
* sudo systemctl status tomcat
