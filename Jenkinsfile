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
               'git checkout master'
               'git checkout dev'
               'git merge master'
           }
       }
    }
}
