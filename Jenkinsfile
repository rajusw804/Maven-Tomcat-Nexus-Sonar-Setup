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
   
          post {
                success {
                    echo 'archiving....'
                    archiveArtifacts artifacts: '**/*.war', followSymlinks: false
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

stage('SonarQube scanning') {
            steps {
                withSonarQubeEnv('sonar_scanner') {
                    withCredentials([string(credentialsId: 'jenkins-maven', variable: '34e2006abd0d7e33a0df1ef63bba2cd10aaff906')]) {
                        sh """
                    mvn sonar:sonar \
                    -Dsonar.projectKey=maven \
                    -Dsonar.host.url=http://52.91.126.158:9000 \
                    -Dsonar.login=$SONAR_TOKEN
                    """
                    }
                }
            }
        }
}
}
