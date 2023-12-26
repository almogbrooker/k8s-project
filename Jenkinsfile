pipeline{
    agent{
        label "Jenkins-Agent"
    }
    tools {
        jdk 'Java17'

    }
    stages{

        stage("Clean Workspace"){
            steps{
               cleanWs()
            }
        }

        stage("Checkout from SCM"){
            steps{
                git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/almogbrooker/k8s-project'
            }
        }

        stage("Build Docker Images"){
            steps{            
                    // Build Docker image for Producer
                    sh 'docker-compose -f docker-compose.yml build'

            }
        }
        stage('Push Docker Images') {
            steps {
                    sh 'docker images'
                    // Push Docker images to a registry (if needed)
                    sh 'docker push coscoson/producer-image:latest'
                    sh 'docker push coscoson/consumer-image:latest'
                
            }
        }
    }
}