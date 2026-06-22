pipeline {
    agent any
    
    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Maven Build') {
            steps {
                echo 'Checking Maven and Java versions...'
                sh 'mvn --version'
                
                // Let's prove the actual compiler matches!
                sh 'javac -version' 
                
                echo 'Building the application with Maven...'
                sh 'mvn clean package -DskipTests=true'
            }
        }
    }
}
