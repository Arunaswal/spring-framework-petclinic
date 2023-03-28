pipeline {
    agent any
    options { timeout(time: 1, unit: 'HOURS') }
    triggers { cron('0 * * * *') }
    stages {
       stage('get the code from git') {
         steps {
            echo "clone from git"
            git url: 'https://github.com/Arunaswal/spring-framework-petclinic.git',
            branch: 'main'
         }
        }
        stage('build the code'){
            steps {
            echo "building the code"
            sh script: '/opt/apache-maven-3.9.1/bin/mvn clean package'
            }
        }
        stage('archiving the artifact and test'){
            steps {
            echo "archiving the artifact"
            junit testResults: '/target/surefire-report/*.xml'
            }
        }
    }   
}
