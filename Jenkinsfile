pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    whoami

                    npm ci

                    npm run build
                '''
                
            }
        }

        stage('Test'){
            steps{
                echo 'Test stage'
            }
        }
    }
    
}
