pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://F64A735801D43B95C0538AB2A6CBCA6E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://F64A735801D43B95C0538AB2A6CBCA6E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                    
                }
            }
        }
    }
}
