pipeline {
    agent any
    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/ashithss/docker-java.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t java_application:${BUILD_NUMBER} .'
            }
        }
        stage("Docker HUB Login"){
            steps{
                sh 'sudo aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 897722692916.dkr.ecr.ap-south-1.amazonaws.com'
            }
        }
        stage("Tag Docker image"){
            steps{
                sh 'sudo docker tag java_application:${BUILD_NUMBER} 897722692916.dkr.ecr.ap-south-1.amazonaws.com/java_application:${BUILD_NUMBER}'
            }
        }

        stage("Push Docker Image"){
            steps{
                sh 'sudo docker push 897722692916.dkr.ecr.ap-south-1.amazonaws.com/java_application:${BUILD_NUMBER}'
            }
        }

        stage('K8S Deploy') {
            steps{   
                script {
                    sh "sudo aws eks --region ap-south-1 update-kubeconfig --name wonderful-pop-painting"
                    // sh "sudo kubectl apply -f /var/www/html/k8s-manifestfiles/IN/qa/ai-Signature-Verification-QA/dep-signature-verification.yaml" 
                   // sh "sudo kubectl set image deployments/dep-ai-signature-verification-qa img-ai-signature-verification=${registry}:${BUILD_NUMBER} -n qa-eks"
                }
                
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
