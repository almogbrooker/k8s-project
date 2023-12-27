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

        stage("Clone From Github"){
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
                    // Push Docker images to a registry (if needed)
                    sh 'docker push coscoson/producer-image:latest'
                    sh 'docker push coscoson/consumer-image:latest'
            }
        }
        stage('Deploy RabbitMQ') {
            steps {
                script {
                    // Add the RabbitMQ Helm repository
                    sh 'helm repo add bitnami https://charts.bitnami.com/bitnami'
                    
                    // Install RabbitMQ using Helm
                    sh 'helm install my-rabbitmq bitnami/rabbitmq'
                }
            }
        }
        
    }
}