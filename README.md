yum install git maven java-openjdk11 tree -y

sudo yum install tomcat tomcat-webapps tomcat-admin-webapps tomcat-docs-webapp tomcat-javadoc -y

systemctl start tomcat

systemctl enable tomcat

vi /usr/share/tomcat/conf/tomcat-users.xml

<role rolename="tomcat"/>

<role rolename="admin-script"/>

<role rolename="manager-script"/>

<role rolename="manager-gui"/>

<role rolename="manager-jmx"/>

<role rolename="manager-status"/>

<role rolename="manager"/>

<role rolename="admin"/>

<user password="password" roles="tomcat" username="admin"/>

<user password="password" roles="manager-gui" username="admin"/>

<user password="password" roles="admin,admin-script,manager-gui,manager-script,manager-jmx,manager-status" username="admin"/>

:wq!

systemctl restart tomcat

 vi /etc/maven/settings.xml
       <server>
      <id>TomcatServer</id>
      <username>admin</username>
      <password>password</password>
    </server>

mvn install tomcat7:deploy

/usr/share/tomcat
bin  conf  lib  logs  temp  webapps  work

cd java-docker-project

mvn package

cp target/java-tomcat-maven-example.war /usr/share/tomcat/webapps/


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
