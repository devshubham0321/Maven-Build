pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/<your-username>/Maven-Build.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                sh '''
                scp -o StrictHostKeyChecking=no -P $PORT target/*.war $USERNAME@$HOST:/opt/tomcat/webapps/
                           }
        }
    }
    environment {
        HOST = credentials('tomcat-host')
        USERNAME = credentials('tomcat-user')
        PORT = '22'
    }
}
