pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2338E92A19C7A592664E69793AF487FB.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
         stage('verfy deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2338E92A19C7A592664E69793AF487FB.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
