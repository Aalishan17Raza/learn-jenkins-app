pipeline {
    agent any
    stages {
        stage('build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                echo 'docker running fine'
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

        stage('build test') {
            sh '''
                [ -f /build/index.html ] && echo "file exists" || echo "file doesn't exist"
                npm test 
            '''
        }
    }
}
