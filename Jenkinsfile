pipeline {
    agent any

    stages {

        stage('Deploy Kubernetes') {
            agent {
                kubernetes {
                    cloud 'kubernetes'
                }
            }
            environment {
                tag_version = "${env.BUILD_ID}"
            }

            steps {
                sh 'sed -i "s/{{tag}}/$tag_version/g" ./k8s/n8n.yaml'
                sh 'cat ./k8s/n8n.yaml'
                kubernetesDeploy(configs: '**/k8s/n8n.yaml', kubeconfigId: 'kubeconfig')
            }
        }
    }
}
