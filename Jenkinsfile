pipeline {
    agent { 
    	docker { image 'java:openjdk-8-jdk' } 
    }

    triggers { 
        pollSCM('* * * * *') 
    }

    stages {
        stage('Build') { 
            steps { 
                sh 'ls'
                sh 'pwd'
                sh './gradlew clean build'
            }
        }

        stage('Release'){
            steps{
                archiveArtifacts artifacts: 'service-jersey-app/build/distributions/*.zip'
            }
        }

        stage('Deploy PROD') {
            steps {
                timeout(time:1, unit:'DAYS') {
                    input message: 'Are you sure?'
                } 
                sshagent (credentials: ['servidor-treinamento']) {            
                     sh 'scp -o StrictHostKeyChecking=no  service-jersey-app/build/distributions/service-jersey-app-1.1.zip ubuntu@172.31.9.116:~'
                     sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.116 "unzip service-jersey-app-1.1.zip"'
                }
            }
        }
    }
}