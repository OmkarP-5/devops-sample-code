pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out the repository...'
                git url: 'https://github.com/OmkarP-5/devops-sample-code.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies globally...'
                sh '''
                python3 -m pip install --upgrade pip  # Upgrade pip
                pip3 install -r requirements.txt      # Install required dependencies
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh '''
                python3 -m unittest discover -s .  # Run tests
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
