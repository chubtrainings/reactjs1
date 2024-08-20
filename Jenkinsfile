pipeline {
    agent any

   

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git credentialsId: 'token', url: 'https://github.com/chubtrainings/reactjs1.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run build commands here
                    // Example: sh 'npm install'
                    echo 'Building the project...'
                    // Add your build commands here
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests here
                    // Example: sh 'npm test'
                    echo 'Running tests...'
                    // Add your test commands here
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy the application here
                    // Example: sh './deploy.sh'
                    echo 'Deploying the application...'
                    // Add your deploy commands here
                }
            }
        }
    }

    post {
        success {
            // Actions to perform on successful build
            echo 'Build succeeded!'
        }
        failure {
            // Actions to perform on failed build
            echo 'Build failed.'
        }
        always {
            // Actions to perform regardless of the build result
            echo 'Cleaning up...'
        }
    }
}
