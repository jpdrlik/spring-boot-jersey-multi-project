pipeline {
    agent any

    stages {
        stage('Build') {
            steps { 
               ./gradlew clean build
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
