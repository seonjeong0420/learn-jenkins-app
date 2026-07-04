pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }

    environment {
        BUILD_FILE_NAME = 'index.html'
    }

    stages {
        stage('Build') {
            
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage ('Test') {
            steps {
                echo 'Test stage'
                sh '''
                    test -f build/$BUILD_FILE_NAME
                    npm test
                '''
            }
        }
    }
}
