pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
       stage('Merge master') {
           steps{
               sh 'git fetch --all'
               sh 'git checkout master'
               sh 'git checkout dev'
               sh 'git merge master'
           }
       }
    }
}
