pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksdemo1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9249BD6716E2CB202D29C4C033C52BCC.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksdemo1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9249BD6716E2CB202D29C4C033C52BCC.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
