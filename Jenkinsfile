ipeline {
    agent any

    tools {
        maven 'M2_HOME' // Define your Maven installation name from Jenkins -> Global Tool Configuration
    }

    environment {
        DEPLOY_SERVER = '13.218.235.192'
        DEPLOY_USER = 'ubuntu'
        DEPLOY_PATH = '/home/ubuntu/tomcat8/webapps'
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/Dinesh2002-git/dinesh.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sshagent(credentials: ['tomcat-ssh-key']) {
                    sh """
                        scp target/*.war $/var/lib/jenkins/workspace/app-deploy@$ubuntu@13.218.235.192:$/home/ubuntu/tomcat8/webapps/
                    """
                }
            }
        }
    }



