pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'raham-cluster', contextName: '', credentialsId: 'svcact.tokentok8s', namespace: 'webapps', serverUrl: 'https://8A803075B652A4D167F41733DE3BC1C9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'raham-cluster', contextName: '', credentialsId: 'svcact.tokentok8s', namespace: 'webapps', serverUrl: 'https://8A803075B652A4D167F41733DE3BC1C9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
