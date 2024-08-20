pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-personal-access-token', url: 'https://github.com/chubtrainings/reactjs1.git', branch: 'main'
            }
        }
        // Other stages
    }
}
