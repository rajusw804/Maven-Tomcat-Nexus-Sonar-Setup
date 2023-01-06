pipeline {
    agent any

    stages {
        stage('clone github code') {
            steps {
                // Get some code from a GitHub repository
                sh 'git clone https://github.com/rajulucky812/jenkins-docker-project.git'
            }

        stage('compile') {
            steps {

                sh 'mvn compile'
            }
			}
       stage('package') {
            steps {

                sh 'mvn package'
            }
			
        }
    }
}
}
