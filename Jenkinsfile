pipeline {
    agent any

     environment {
            CI = 'true'
        }
    stages {
        stage('Build') {
            steps {
                nodejs('Node') {
                sh 'npm install'
                     args '-p 3000:3000'
            }
        }
        } 
        stage('Test') {
                    steps {
                        nodejs('Node') {
                        sh './jenkins/scripts/test.sh'
                        }
                    }
                }
                stage('Deliver') {
                            steps {
                                nodejs('Node') {
                                sh './jenkins/scripts/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh './jenkins/scripts/kill.sh'
                                }
                            }
                        }

    }
}

