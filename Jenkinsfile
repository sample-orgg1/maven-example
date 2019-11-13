pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                sh 'echo code checkout'
                git credentialsId: 'githubID', url: 'https://github.com/itrainpulsars/maven-example.git'
            }
        }
        stage('Build') { 
            steps {
              withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn clean compile'
             } 
            }
        }
        stage('Test') { 
            steps {
               withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn test'
             }  
            }
        }
        stage('Package') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn package'
             }  
            }
        }
        stage('code analysis') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn sonar:sonar' \
  -Dsonar.projectKey=maven-example-11 \
  -Dsonar.organization=sample-orgg1 \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=fc1ccb5a3449ac85a4beaa9abb21a32d3ad8e851
             }  
            }
        }
        
        stage('Docker Image') { 
            steps {
                sh 'echo Docker Image' 
            }
        }
        stage('Deploy to Dev') { 
            steps {
                sh 'echo Deploy to Dev' 
            }
        }
        stage('Deploy to Prod') { 
            steps {
                sh 'echo Deploy to Prod' 
            }
        }
    }
}
