pipeline {
    agent { label 'JDK11'}
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('sourcecode') {
            steps {
                git url: 'https://github.com/Prasadsgithub/spring-petclinic.git', 
                branch: 'sprint_1_dev'
            }   
        }
        stage('Build the Code and sonarqube-analysis') {
            steps {
                withSonarQubeEnv('SONAR_LATEST') {
                    sh script: "mvn clean package sonar:sonar"
                }
            }
        }
        stage('reporting') {
            steps {
                junit testResults: '**/surefire-reports/*.xml'
            }
        }
    }
}