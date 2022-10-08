pipeline {
    agent { label 'JDK11'}
    options {
        timeout(time: 1, unit: 'HOURS')
        retry(3)
    }
    triggers {
        cron('H * * * *')
        pollSCM('* * * * *')
    }
    stages {
        stage('sourcecode') {
            steps {
                git url: 'https://github.com/Prasadsgithub/spring-petclinic.git', 
                branch: 'features'
            }    
        }
        stage('Build the code') {
            steps {
                sh script: 'mvn clean package'
            }
        }    
        stage('reporting') {
            steps {
                junit testresults: 'target/surefire-reports/*.xml'
            }
        }
    }
}