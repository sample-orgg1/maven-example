pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                sh 'echo code checkout'
                git credentialsId: 'github-anubhav', url: 'https://github.com/sample-orgg1/maven-example.git'
            }
        }
        stage('Build') { 
            steps {
              withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
               sh 'mvn clean compile'
             } 
            }
        }
        stage('Test') { 
            steps {
               withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
               sh 'mvn test'
             }  
            }
        }
        stage('Package') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
               sh 'mvn package'
             }  
            }
        }
        stage('code analysis') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
               sh 'mvn sonar:sonar \
                 -Dsonar.projectKey=maven-anubhav \
                 -Dsonar.organization=sample-orgg1 \
                 -Dsonar.host.url=https://sonarcloud.io \
                 -Dsonar.login=fc849f7380c469698ba457e70b02dd2c9d815654'
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
