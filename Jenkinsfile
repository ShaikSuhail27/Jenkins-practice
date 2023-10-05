pipeline {
    agent { node { label 'Agent-1' } }

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
    }
    post { 
        always { 
            echo 'it will always run whether it is success or not'
        }
        success{
            echo 'it will run if it is success'
        }
        failure{
            echo 'it will run if it is failure'
        }
    }
}
