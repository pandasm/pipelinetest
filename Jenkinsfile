pipeline {
    agent any
    stages {
        stage('Preparation') { 
             steps {
              // Get some code from a GitHub repository
              git 'https://github.com/pandasm/pipelinetest.git'
             }
        }
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}