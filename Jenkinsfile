pipeline {
    agent any
    stages {
        stage('Preparation') { 
             steps {
              // Get some code from a GitHub repository
              git 'https://github.com/pandasm/pipelinetest.git'
             }
        }
        stage('Spinup-Containers') { 
            steps {
                sh './configurations/docker-compose up' 
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
        stage('Destroy-Containers') { 
            steps {
                sh 'docker stop $(docker ps -a -q)'
                sh 'docker rm $(docker ps -a -q)'
            }
        }
    }
}