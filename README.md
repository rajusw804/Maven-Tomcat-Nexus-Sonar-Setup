yum install git maven java-openjdk11 tree -y

sudo yum install tomcat tomcat-webapps tomcat-admin-webapps tomcat-docs-webapp tomcat-javadoc -y

systemctl start tomcat

systemctl enable tomcat

/usr/share/tomcat

bin  conf  lib  logs  temp  webapps  work


# jenkins-docker-project

Maven:

POM.XML   

extensible markup Lanaguage

Project object Model 

Lifecycle Phases :

Compile

Test : Target with surefire report

Package : war/jar/ear


clean : Deleteing target folder

Repositories: 3 

Remote : Other server

Local : /root/.m2/

Centeral : https://repo.maven.apache.org/maven2/org/

--------------------------------------
