pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Listing workspace files:"
                    ls -la
                    echo "Node.js and npm versions:"
                    node --version
                    npm --version
                    echo "Installing dependencies:"
                    npm ci
                    echo "Building the application:"
                    npm run build
                    echo "Final workspace files:"
                    ls -la
                '''
            }
        }
    }
    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
