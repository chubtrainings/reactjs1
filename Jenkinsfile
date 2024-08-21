pipeline {
    agent any
    
    environment {
      //  GIT_CREDENTIALS = 'github-personal-access-token' // Update with your credentials ID
      //  REPO_URL = 'https://github.com/chubtrainings/reactjs1.git' // Update with your repo URL
        BRANCH = 'main' // Update with your branch name
      //  DOCKERHUB_CREDENTIALS = 'dockerhubcreds' // Update with your Docker Hub credentials ID
        DOCKER_IMAGE = 'prathin2023/reactapp' // Update with your Docker Hub username and image name
        
    }
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'token', url: 'https://github.com/chubtrainings/reactjs1.git', branch: 'main'
                sh 'ls -al'
                
            }
        }
        // Other stages

        stage('Build') {
            steps {
                script {
                    // Run build commands here
                    // Example: sh 'npm install'
                    sh 'docker images'
                 //   sh 'docker build -t prathin2023/reactapp .'
                    sh 'docker images'
                    
                    echo 'Building the project...'
                    // Add your build commands here
                }
            }
        }
        // Other stages
        
        stage('Tag and Push') {
            steps {
                script {
                    def tagName = "v${env.BUILD_NUMBER}"
                    echo "Creating Git tag: ${tagName}"
                    
                    // Docker login
                    echo "Logging into Docker Hub..."
                    withCredentials([usernamePassword(credentialsId: 'dockerhubcreds', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')])
                     {
                         
                         sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
                     }
    
                    
                    // Tag and push the Docker image
                    echo "Tagging Docker image with: ${tagName}"
                    sh "docker build -t ${DOCKER_IMAGE}:${tagName} ."
                 //   sh "docker push ${DOCKER_IMAGE}:${tagName}"
                    echo "The Docker Iamge create is ${DOCKER_IMAGE}:${tagName} will be pushed to Dockerhub"
                    // Optionally, tag and push the "latest" tag
                //    echo "Tagging Docker image with: latest"
                    sh "docker tag ${DOCKER_IMAGE}:${tagName} ${DOCKER_IMAGE}:latest"
                    sh "docker push ${DOCKER_IMAGE}:latest"
                }
            }
        }

        // Other stages
    }
    post{
    always {  
	sh 'docker logout'     
    }      
    }  
}
