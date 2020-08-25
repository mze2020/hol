pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
      
    stages {
        
        stage('build') {
            steps {
                echo 'Hello World'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
    stage('test') {
            steps {
                sh 'mvn test'   
                  
            }
        }
    stage ('build and publish image') {
  steps {
    script {
          checkout scm
          docker.withRegistry('', 'DockerRegistryID') {
          def customImage = docker.build("mze2020/hol-pipeline:${env.BUILD_ID}")
          customImage.push()
          }
    }
        
    }
}
    }
}

