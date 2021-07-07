pipeline {
    agent any
    environment {
        PROJECT_ID = 'java-app-315716'
        CLUSTER_NAME = 'cluster-1'
        LOCATION = 'us-east4'
        CREDENTIALS_ID = 'java-app-315716'
    }
    stages {
        stage('Deploy to GKE') {
            steps{
                sh "sed -i 's/tagversion/${env.Build_Number}/g' deployment.yaml"
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'deployment.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
            }
        }
    }    
}
