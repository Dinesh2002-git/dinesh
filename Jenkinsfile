pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    environment {
        MVN_CREDENTIALS = credentials('nexus-creds')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo "Deployment to Tomcat placeholder"
                // Optional: SCP or Curl deploy WAR to Tomcat webapps
            }
        }
    }
}
