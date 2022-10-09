## Jenkins Git Maven Sonarqube Docker and AWS ECR SES

There are two server on aws 
### jenkin server ( Ram 2) and sonarqube server ( Ram 4 ) Minimum
## On Jenkins server
root user
```
sudo -i
```

## ON jenkins server
### java and jenkins install
https://github.com/mydev911/Jenkins/blob/main/Jenkins_install/Jenkins_install_aws.md
### Git install
```
yum install git -y
```
### Maven install
https://github.com/mydev911/Jenkins/blob/main/Maven_install_jenkins.md

### Docker install
https://github.com/mydev911/Docker_example/blob/main/Install_docker/install_docker_1.md

### we need to give docker permission
```
su ec2-user
```
```
sudo chmod 777 /var/run/docker.sock
```

##### On jenkins web
Global Tool Configuration > Maven > Add Maven > 
Name > apache-maven-3.8.6
MAVEN_HOME
/opt/apache-maven-3.8.6
### sonar-scaner plugin install


## ON sonarqube server

### Sonarqube install
https://github.com/mydev911/SonarQube/blob/main/Sonarqube/Setup_SonaQube_Aws.md

##### Install docker
https://github.com/mydev911/Docker_example/blob/main/Install_docker/install_docker_1.md

### we need to give docker permission ( we can not run sonaqube on root user)
```
su ec2-user
```
```
sudo chmod 777 /var/run/docker.sock
```

### webhook on sonarqube
jenkins_IP/sonarqube-webhook/












