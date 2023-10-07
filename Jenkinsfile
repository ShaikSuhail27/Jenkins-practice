pipeline {
    agent { node { label 'Agent-1' } }
    // triggers {
    //     cron('* * * * *')
    // }
    options {
        ansiColor('xterm')
    }
    environment { 
        USER = 'suhail'
    }
     parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                echo 'doing the building'

                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                 sh '''
                echo 'doing the testing'
                
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('parameter values') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
        stage('Prod') {
            when {
                environment name: 'USER', value: 'suhail'
            }
            steps {
                echo 'Deploying to production'
            }
        }
        stage('Parallel Stage') {
            parallel {
                stage('Branch A') {
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Branch C') {
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                            }
                        }
                    }
                }
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
