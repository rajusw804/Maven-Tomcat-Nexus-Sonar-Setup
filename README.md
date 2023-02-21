yum install git maven java-openjdk11 tree -y

sudo yum install tomcat tomcat-webapps tomcat-admin-webapps tomcat-docs-webapp tomcat-javadoc -y

systemctl start tomcat

systemctl enable tomcat

----------------------------------------------------------------------------------------------------------------------

Jenkins installation:

sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo

sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key 

sudo yum -y install jenkins -y

echo "--------Jenkins,Java installed"

sudo systemctl enable jenkins

sudo systemctl start jenkins

----------------------------------------------------------------------------------------------------------------------

vi /usr/share/tomcat/conf/tomcat-users.xml

:wq!

systemctl restart tomcat

 vi /etc/maven/settings.xml

mvn install tomcat7:deploy


mvn package

cp target/java-tomcat-maven-example.war /usr/share/tomcat/webapps/

----------------------------------------------------------------------------------------------------------------------

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
