pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6B731E0ED65BE5C1F1C9CE1E26C8C6DC.gr7.ap-south-1.eks.amazonaws.com']]) {
                        sh "kubectl apply -f deployment-service.yml"
                    }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6B731E0ED65BE5C1F1C9CE1E26C8C6DC.gr7.ap-south-1.eks.amazonaws.com']]) {
                        sh "kubectl get svc -n webapps"
                    }
            }
        }
    }
}
