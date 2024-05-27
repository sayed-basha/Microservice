pipeline {
    agent any

    stages {
        stage('deploy') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: 'EKS-1', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E29643FA9A64AB8E611F2E157F1C0808.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
               }
            }
        }
        
        
        stage('verify') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: 'EKS-1', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E29643FA9A64AB8E611F2E157F1C0808.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                 }
            }
        }
    }
}
