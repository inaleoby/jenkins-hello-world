pipeline {
  agent any
  stages {
    stage('MAVEN VERSION') {
      steps {
        sh ' echo print maven version'
        sh 'mvn -version'
      }
    }

    stage('BUILD') {
      steps {
        sh 'git clone https://github.com/inaleoby/jenkins-hello-world.git'
        dir(path: 'jenkins-hello-world') {
          sh 'mvn clean package -DskipTests=true'
        }

        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('TEST') {
      steps {
        dir(path: 'jenkins-hello-world') {
          sh 'mvn test'
        }

        junit(testResults: '/target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
      }
    }

  }
  tools {
    maven 'M3910'
  }
}