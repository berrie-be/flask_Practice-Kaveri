pipeline {
    agent any
    triggers {
        githubPush()
    }
    environment {
        MONGO_URI = credentials('MONGO_URI')
        SECRET_KEY = credentials('SECRET_KEY')
    }
    stages {
        stage('Build') {
            when {
                anyOf {
                    branch 'origin/main'
                    branch 'origin/staging'
                }
            }
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip3 install -r requirements.txt
                '''
            }
          
        }
        stage('Test') {
            when {
                branch 'origin/staging'
            }
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
          
        }
        stage('Deploy') {
            when {
                anyOf {
                    branch 'origin/main'
                    branch 'origin/staging'
                }
            }            
            steps {
                sh '''
                docker build -t test:01 .
                docker run -itd -e MONGO_URI="$MONGO_URI" -e SECRET_KEY="$SECRET_KEY" -p 5000:5000 test:01
                sleep 5
                curl http://localhost:5000/
                '''
            }
          
        }
    }
}
