pipeline {
    agent any
    environment {
        CSRF_TOKEN = credentials('CSRF_TOKEN')
    }
    stages {
        stage('Create Secret') {
            steps {
                    sh "sed -e 's,{{SECRET_KEY}}, '${csf_token}' ,g;' credentials.yaml  kubectl apply -f -"
            }
        }
        stage('Deploy App') {
            steps {
                sh "kubectl apply -f todo.yaml"
                
            }
        }
    }
}