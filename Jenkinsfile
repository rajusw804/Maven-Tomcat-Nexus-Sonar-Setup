pipeline {
    agent any
    stages {
        stage("Clone code from GitHub") {
            steps {
                script {
                    git url: 'https://github.com/knowledgemate/Maven-Tomcat-Setup.git', branch: 'main'
                }
            }
        }
        stage("Maven Build") {
            steps {
                script {
                    sh "mvn clean package"
                }
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('Checkstyle Code Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Generated Analysis Result'
                }
            }
        }
      stage('SonarScanning') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=f5782cfeafd95d3216f992b6c35bbdfe5fd67ac3'
            }
			}
        
      stage("Publish to Nexus Repository Manager") {
            steps {
            sh 'mvn clean deploy'
            }
            }
      stage("Deploy it to tomcat") {
            steps {
            sh 'ssh -t -t root@18.206.198.11 -o StrictHostKeyChecking=no "mvn install tomcat7:deploy"'
            }
        }
}
}
