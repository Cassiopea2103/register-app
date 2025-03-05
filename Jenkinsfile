pipeline {
    agent {
        label 'jenkins-worker'
    }
    tools {
        jdk 'jdk-17' 
        maven 'maven3'
    }
    stages {
        stage ('Workspace cleanup') {
            steps {
                echo 'Cleaning workspace...'
                cleanWs()
            }
        }
        stage ('Checkout github repository'){
            steps {
                echo 'Checking out the repository...'
                steps {
                    git branch : 'main' , credentialsId : 'github-credentials' , url : 'https://github.com/Cassiopea2103/register-app.git'
                }
            }
        }
        stage ('Application build'){
            steps {
                echo 'Building the application...'
                sh 'mvn clean package' 
            }
        }
        stage ('Application test'){
            steps {
                echo 'Testing the applicaton'
                sh 'mvn test' 
            }
        }
    }
}