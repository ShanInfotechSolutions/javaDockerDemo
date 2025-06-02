pipeline {
  agent any

  tools {
    maven 'Maven_3'
    jdk 'JDK_17'
  }

  environment {
    IMAGE_NAME = "shaninfotech/dockerintegratingdemo/java-maven-app"
    TAG = "latest"
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main',
            url: 'https://github.com/ShanInfotechSolutions/javaDockerDemo.git'
      }
    }

    stage('Build with Maven') {
      steps {
        // No need for dir(), since pom.xml is at repo root
        sh 'mvn clean package'
      }
    }

    stage('Build Docker Image') {
      steps {
        // Dockerfile is also at the root
        sh 'docker build -t $IMAGE_NAME:$TAG .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run --rm $IMAGE_NAME:$TAG'
      }
    }
  }
}
