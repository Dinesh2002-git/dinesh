pipeline {
  agent any

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
        sh '''
        ssh-keyscan -H 172.31.87.228 >> ~/.ssh/known_hosts
        scp /var/lib/jenkins/workspace/app-deploy/target/*.war ubuntu@172.31.87.228:/home/ubuntu/tomcat8/webapps/
        '''
      }
    }
  }
}
