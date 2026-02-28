pipeline {
    agent any

    stages {
        stage('deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2084B05A79C264F6C1F4C476A41C5758.yl4.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 70
               
            }
        }
    }    
            stage('verify deployment') {
             steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2084B05A79C264F6C1F4C476A41C5758.yl4.ap-south-1.eks.amazonaws.com']])  {
                 sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
