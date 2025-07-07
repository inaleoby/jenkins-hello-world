pipeline {
    agent any
    tools {
        maven "M3910"
    }
    stages {
        stage('MAVEN VERSION') {
            steps {
                sh " echo print maven version"
                sh "mvn -version"
            }
        }
        
        stage('BUILD') {
            steps {
                sh "git clone https://github.com/inaleoby/jenkins-hello-world.git"
                dir('jenkins-hello-world') {
                    sh "mvn clean package -DskipTests=true"
                }
            }
        }
        stage('TEST') {
            steps {
                  dir('jenkins-hello-world') {
                      sh "mvn test"
                }
            }
        }
    }
}
