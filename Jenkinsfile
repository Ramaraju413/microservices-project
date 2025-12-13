pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://4C00031A91D9DAB026F344F1903940CB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://4C00031A91D9DAB026F344F1903940CB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
