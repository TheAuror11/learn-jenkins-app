pipeline {
    agent any

    stages {

        stage('Pre Build'){
            steps{
                sh '''
                    echo "Pre Build"
                    echo Build Id: ${BUILD_ID}
                    echo Build URL: ${BUILD_URL}
                '''
            }
        }
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
            agent {
                docker {
                    image 'node:22-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
    
}
