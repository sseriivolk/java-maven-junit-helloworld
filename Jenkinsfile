pipeline {
    agent any
    tools {
        maven 'Maven'
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
                jdk 'JDK8'
            }
            steps {
                sh 'mvn install'
            }
        }
        stage('SonarQube') {
            tools{
                jdk 'JDK11'
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
}
