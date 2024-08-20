pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'token', url: 'https://github.com/chubtrainings/reactjs1.git', branch: 'main'
            }
        }
        // Other stages

        stage('Build') {
            steps {
                script {
                    // Run build commands here
                    // Example: sh 'npm install'
                    sh 'docker images'
                    
                    echo 'Building the project...'
                    // Add your build commands here
                }
            }
        }
        // Other stages
    }
}
