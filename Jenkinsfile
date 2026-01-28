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
                docker run -itd -e MONGO_URI="$MONGO_URI" -e SECRET_KEY="$SECRET_KEY" -p 5000:5000 test:01
                sleep 5
                curl http://localhost:5000/
                '''
            }
          
        }
    }
    post {
    success {
        sh """
        aws sns publish \
          --region us-west-1 \
          --topic-arn arn:aws:sns:us-west-1:975050024946:jenkins-build-notifications \
          --message "✅ SUCCESS: Job ${env.JOB_NAME} #${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME}"
        """
    }

    failure {
        sh """
        aws sns publish \
          --region us-west-1 \
          --topic-arn arn:aws:sns:us-west-1:975050024946:jenkins-build-notifications \
          --message "❌ FAILURE: Job ${env.JOB_NAME} #${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME}"
        """
    }
}
}
