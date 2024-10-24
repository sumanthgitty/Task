pipeline {
    agent any
    
    stages {
        stage('Stop Deployment') {
            steps {
                // Add commands to stop the running deployment
                sh 'sudo pm2 delete static-page-server-8081'
            }
        }
        stage('Pull Code') {
            steps {
                // Pull fresh code from your Git repository to /opt/checkout/react-todo-add
                dir('/opt/checkout/react-todo-add') {
                    sh 'sudo git clone https://github.com/kabirbaidhya/react-todo-app'
                }
            }
        }
        stage('Build') {
            steps {
                // Build your application
                dir('/opt/checkout/react-todo-app') {
                    sh 'sudo npm install' // or any build commands you need
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application using pm2 /Demo to check PR 
                dir('/opt/deployment/react') {
                    sh 'sudo pm2 serve . 8081 --spa' // Start the application
                }
            }
        }
    }
}
