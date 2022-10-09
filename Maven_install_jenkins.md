## Install maven on jenkins
https://www.fosstechnix.com/how-to-install-maven-on-ubuntu/

https://maven.apache.org/download.cgi
Root > opt
```
cd /opt
```
```
wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
```
```
ls
```
```
tar -xvf apache-maven-3.8.6-bin.tar.gz
```
Remove tar file
```
rm -rf apache-maven-3.8.6-bin.tar.gz
```
### Now setup the path for maven

##### Temporily setup for maven path
```
export PATH=$PATH:/opt/apache-maven-3.8.6/bin
```
```
mvn --version
```
##### Permanant setup for maven path
```
vi ~/.bashrc
```
Paste this command
```
export PATH=$PATH:/opt/apache-maven-3.8.6/bin
```
```
source ~/.bashrc
```
