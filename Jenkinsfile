pipeline {
    agent any
    triggers {
        githubPush()
    }
    environment {
        MONGO_URI = credentials('MONGO_URI')
        SECRET_KEY = credentials('SECRET_KEY')
        HOST_PORT = "${env.BRANCH_NAME == 'staging' ? '5000' : '5001'}"
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip3 install -r requirements.txt
                '''
            }
          
        }
        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
          
        }
        stage('Deploy') {
            steps {
                sh '''
                docker build -t test:01 .
                docker run -itd -e MONGO_URI="$MONGO_URI" -e SECRET_KEY="$SECRET_KEY" -p $HOST_PORT:5000 test:01
                sleep 5
                curl http://localhost:5000/
                '''
            }
          
        }
    }
}
