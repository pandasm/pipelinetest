pipeline {
    agent any
    stages {
        stage('Pull latest Code') { 
             steps {
              // Get some code from a GitHub repository
              git 'https://github.com/pandasm/pipelinetest.git'
             }
        }
		stage('spinning up docker images'){
        	steps {
                	sh 'docker-compose up -d' 
             }	
        }
     
        stage('Build') { 
            steps {
            	sh 'export JAVA_HOME=$(/usr/libexec/java_home)'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Destroy - After Running tests on Containers') { 
            steps {
                sh 'docker stop $(docker ps -a -q)'
                sh 'docker rm $(docker ps -a -q)'
            }
        }
    }
}