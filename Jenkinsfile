pipeline {
    agent {
        label = "k8s-slave"
    }
    environment {
        APPLICATION_NAME = "eureka"
    }   
    tools {
        maven "Maven-3.8.8"
        jdk 'java-17'
    }                                
    stages {
        stage ('Build the application... ${env.APPLICATION_NAME}') {
            steps {
                echo "Building..."
                sh "maven clean packages"
            }
        }
        stage ('Unit Test') {
            steps {
                echo "Running Unit test for application...${env.APPLICATION_NAME}"
                sh "maven test"
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
     }
    }

 