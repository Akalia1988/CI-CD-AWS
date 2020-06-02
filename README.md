# DevOps CI/CD pipelines using Git, Jenkins, Ansible, Docker and Kubernetes on AWS please refer to the zip file ( devops project which explains how to install certain services on AWS (LINUX) 

section 1 CI/CD pipeline using GIT, Jenkins and Maven 

Section 2 Integrating Tomcat server in CI/CD pipeline 

Section 3 Integrating Docker in CI/CD pipeline 
(in the latest version of tomcat apache data is getting stored in webapps.dist file instead of webapps that's why sometimes we are unable to access webapp from browser in order to correct it please follow the steps below.

first you have to run docker container in detached mode

docker run -d --name tomcat-container -p 8080:8080 tomcat

in the latest version of tomcat apache data is getting stored in webapps.dist file instead of webapps that's why sometimes we are unable to access webapp from browser in order to correct it please follow the steps below.

first you have to run docker container in detached mode 

docker run -d --name tomcat-container -p 8080:8080 tomcat

[root@docker ~]# docker run -d --name tomcat-container -p 8080:8080 tomcat
3dcada79db4d54cbb2058afd52e330b448bdbc5a067d31dab0d5e1b098cac5b7
[root@docker ~]# ^C
[root@docker ~]# docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
3dcada79db4d        tomcat              "catalina.sh run"   58 seconds ago      Up 57 seconds       0.0.0.0:8080->8080/tcp   tomcat-container

[root@docker ~]# docker exec -it tomcat-container /bin/bash

root@3dcada79db4d:/usr/local/tomcat# ls

BUILDING.txt     LICENSE  README.md      RUNNING.txt  conf  logs            temp     webapps.dist

CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin          lib   native-jni-lib  webapps  work

root@3dcada79db4d:/usr/local/tomcat# cd webapps

root@3dcada79db4d:/usr/local/tomcat/webapps# ls

root@3dcada79db4d:/usr/local/tomcat/webapps# cd ..
root@3dcada79db4d:/usr/local/tomcat# cd webapp.dist
bash: cd: webapp.dist: No such file or directory
root@3dcada79db4d:/usr/local/tomcat# ls
BUILDING.txt     LICENSE  README.md      RUNNING.txt  conf  logs            temp     webapps.dist
CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin          lib   native-jni-lib  webapps  work
root@3dcada79db4d:/usr/local/tomcat# cd webapps.dist/
root@3dcada79db4d:/usr/local/tomcat/webapps.dist# ls
ROOT  docs  examples  host-manager  manager
root@3dcada79db4d:/usr/local/tomcat/webapps.dist# cp -R * ../webapps

root@3dcada79db4d:/usr/local/tomcat/webapps.dist# cd ../webapps
root@3dcada79db4d:/usr/local/tomcat/webapps# ls
ROOT  docs  examples  host-manager  manager

refresh the browser and you will see the web browser is working now


Section 4 Integrating Ansible in CI/CD pipeline 

Section 5 Integrating Kubernetes in CI/CD pipeline










