pipeline {
    agent {label 'NODE1'}
    
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Code cloning from SCM') {
         steps {
            git url: 'https://github.com/Prasadsgithub/spring-petclinic.git',
            branch: 'main'
           }
        }
        stage("build") {
            steps {
                sh "mvn package"
            }
        }
    }
}