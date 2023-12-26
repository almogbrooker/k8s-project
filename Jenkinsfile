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
    }
}