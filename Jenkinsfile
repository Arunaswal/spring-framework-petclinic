pipeline {
    agent any
    options { timeout(time: 1, unit: 'HOURS') }
    stages {
       stage('get the code from git') {
         steps {
            echo "clone from git"
            git url: 'https://github.com/Arunaswal/spring-framework-petclinic.git',
            branch: 'new-feature'
         }
        }
        stage('build the code'){
            steps {
            echo "building the code new change"
            sh script: '/opt/apache-maven-3.9.3/bin/mvn clean package'
            }
        }
        stage('archiving the artifact and test'){
            steps {
            echo "archiving the artifact"
            junit testResults: '/target/surefire-reports/*.xml'
            }
        }
    }   
}
