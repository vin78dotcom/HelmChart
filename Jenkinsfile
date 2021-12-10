def containerName="docker-pipeline"
def tag="latest"
def dockerHubUser="anujsharma1990"
def httpPort="8090"

node {

    stage('Checkout') {
        checkout scm
    }

    stage('Deploy to Kubernetes'){
        withCredentials([usernamePassword(credentialsId: 'dockerHubAccount', usernameVariable: 'dockerUser', passwordVariable: 'dockerPassword')]) {
            sh "docker login -u $dockerUser -p $dockerPassword"
			sh "kubectl get deployments"
			sh "helm list"
			sh "helm upgrade --install ./counterwebapp --set image.name=${dockerHubAccount}/${containerName} --set image.tag=${tag}"
        }
    }

}
