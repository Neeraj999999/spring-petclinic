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
                echo 'Building the application with Maven...'
                sh 'mvn clean package -DskipTests=true'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube Static Code Analysis...'
                withSonarQubeEnv('sonar-server') {
                    sh 'mvn sonar:sonar -Dsonar.projectKey=spring-petclinic -Dsonar.projectName=spring-petclinic'
                }
            }
        }
    }
}
