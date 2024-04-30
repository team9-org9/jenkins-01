pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-cloning project repo'){
      steps{
       checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/team9-org9/jenkins-chi01.git']])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
    stage('codequality'){
        steps{
      shmvn clean verify sonar:sonar \
  -Dsonar.projectKey=team9 \
  -Dsonar.host.url=http://18.119.107.226:9000 \
  -Dsonar.login=sqp_61a78332ffc8e41b1ca3db63a48874a2f40a1806
      }
    }
  }
}
