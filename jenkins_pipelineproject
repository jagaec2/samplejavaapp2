pipeline {
  environment {
    registry = "yeddula/firstrepo"
    registryCredential = 'dockerhubcred'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/jagaec2/samplejava.git'
      }
    }
    stage('Packaging') {
      steps {
        sh 'mvn package'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":v1"
        }
      }
    }
    stage('Deploy Image to DockerHub repo') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            }
            }
          }
       }     
    }
    
  }
