pipeline {
  agent any

  environment {
    IMAGE_NAME = "shanInfotech/dockerIntegratingDemo/java-maven-app"
    TAG = "latest"
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main',
            url: 'https://github.com/ShanInfotechSolutions/java-docker-jenkins-demo.git'
      }
    }

    stage('Build with Maven') {
      steps {
        dir('javaDockerDemo') {
          sh 'mvn clean package'
        }
      }
    }

    stage('Build Docker Image') {
      steps {
        dir('java8examples/javaPrograms/DockerIntegratingDemo') {
          sh 'docker build -t $IMAGE_NAME:$TAG .'
        }
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run --rm $IMAGE_NAME:$TAG'
      }
    }
  }
}
