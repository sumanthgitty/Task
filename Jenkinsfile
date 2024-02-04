pipeline {
    agent any
    
    stages {
        stage('Stop Deployment') {
            steps {
                // Add commands to stop the running deployment
                sh 'pm2 stop <your_application_name>'
            }
        }
        stage('Pull Code') {
            steps {
                // Pull fresh code from your Git repository to /opt/checkout/react-todo-add
                dir('/opt/checkout/react-todo-add') {
                    git branch: 'main', url: 'https://github.com/your/repo.git'
                }
            }
        }
        stage('Build') {
            steps {
                // Build your application
                dir('/opt/checkout/react-todo-add') {
                    sh 'npm install' // or any build commands you need
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application using pm2
                dir('/opt/deployment/react') {
                    sh 'pm2 start <your_application_name>' // Start the application
                }
            }
        }
    }
}
