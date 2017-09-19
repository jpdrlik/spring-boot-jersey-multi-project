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
                sh 'ls -l'
            }
        }
    }
}
