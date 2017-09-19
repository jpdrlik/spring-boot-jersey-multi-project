pipeline {
    agent any

    stages {
        stage('Build') {
            steps { 
               sh './gradlew clean build'
               sh 'ls -lR'
               echo 'Building...'
            }

        }

        stage('Deploy') {
            steps {
               sshagent (credentials: ['servidor-treinamento']) {
                  sh 'scp ./service-jersey-app/build/distributions/service-jersey-app-1.1.zip ubuntu@172.31.9.116:/home/ubuntu/jean.zip'
                  sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.116 "unzip /home/ubuntu/jean.zip"'            
               }
        }
    }
}
