pipline{
    agent{
        label "Jenkins-Agent"
    }
    tools {
        jdk 'Java17'

    }
    stages{
        stage("Clean Workspace"){
            cleanWs()
        }
    }
    stages{
        stage("Checkout from SCM"){
            steps{
                git branch: 'main', credentialId: 'GitHub', url: 'https://github.com/almogbrooker/k8s-project'
            }
        }
    }
}