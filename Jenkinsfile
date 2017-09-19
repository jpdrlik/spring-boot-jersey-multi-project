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
                  sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.116 "mkdir /hpome/ubuntu/jean"'             
                  sh 'scp ./service-jersey-app/build/distributions/service-jersey-app-1.1.tar ubuntu@172.31.9.116:/home/ubuntu/jean/jean.tar'
                  sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.116 "tar vxf /home/ubuntu/jean/jean.tar"'            
               }
            }
        }
    }
}
