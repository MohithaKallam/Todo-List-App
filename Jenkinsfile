pipeline {
    agent any

    tools {
        nodejs "NodeJS 20"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/MohithaKallam/Todo-List-App.git'
            }
        }

        stage('Backend Install & Test') {
            steps {
                dir('todo-app/backend') {
                    sh 'npm install --legacy-peer-deps'
                    sh 'npm test || true'
                }
            }
        }

        stage('Frontend Install & Test') {
            steps {
                dir('todo-app/frontend') {
                    sh 'npm install --legacy-peer-deps'
                    sh 'npm test -- --watchAll=false || true'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('todo-app/frontend') {
                    sh 'chmod +x node_modules/.bin/react-scripts'
                    sh 'npx react-scripts build'
                }
            }
        }
    }
}
