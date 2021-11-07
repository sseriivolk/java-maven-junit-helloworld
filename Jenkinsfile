pipeline {
    agent any
    tools {
        maven 'mvn3.6.0'
    }

    stages {
        stage('Clone source from Github') {
            steps {
                git branch: 'master',
                url: 'https://github.com/sseriivolk/java-maven-junit-helloworld.git'
                checkout scm  
            }
        }
        stage('Maven Build') {
            tools{
                jdk 'jdk8'
            }
            steps {
                sh 'mvn install'
            }
        }
        stage('SonarQube') {
            tools{
                jdk 'jdk11'
            }
        environment {
            scannerHome = tool 'SonarQube Scanner'
        } 
        steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
            sh 'mvn sonar:sonar'
            }   
        }

    }
}
