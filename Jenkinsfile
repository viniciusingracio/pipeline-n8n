pipeline {
    agent any

    stages {

        stage('Deploy Kubernetes') {
            agent {
                kubernetes {
                    cloud 'kubernetes'
                }
            }
            

            steps {
                kubernetesDeploy(configs: '**/kube/n8n.yaml/')
            }
        }
    }
}
