pipeline {
    agent any
    options { timeout(time: 1, unit: 'HOURS') }
    triggers { cron('0 * * * *') }
    stages {
       stage('get the code from git') {
            echo "clone from git"
            git url: 'https://github.com/Arunaswal/spring-framework-petclinic.git',
            branch: 'main'
        }
        stage('build the code'){
            echo "building the code"
            sh script: mvn clean package
        }
        stage('archiving the artifact and test'){
            echo "archiving the artifact"
            junit testResults: '/target/surefire-report/*.xml'
        }
    }   
}
