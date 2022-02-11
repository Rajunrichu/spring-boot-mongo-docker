pipeline {
    agent any

    tools {
        maven "3.6.0" // You need to add a maven with name "3.6.0" in the Global Tools Configuration page
    }

    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/MithunTechnologiesDevOps/spring-boot-mongo-docker.git',branch: 'master'
    }

    stages {
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean package"
            }
        }
    }

    stage('Build Docker Image'){
        sh 'docker build -t dockerhandson/spring-boot-mongo .'
    }

    post {
        always {
            cleanWs()
        }
    }
}
