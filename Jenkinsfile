pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Building the application with Maven...'
                sh 'mvn clean package -DskipTests=true'
            }
        }
    }
}
