pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out the repository...'
                git url: 'https://github.com/OmkarP-5/devops-sample-code.git', branch: 'main'
            }
        }

        stage('Set up Python Virtual Environment') {
            steps {
                echo 'Setting up virtual environment and installing dependencies...'
                sh '''
                python3 -m venv venv           # Create a virtual environment
                . venv/bin/activate            # Activate the virtual environment
                python3 -m pip install --upgrade pip  # Upgrade pip inside the virtual environment
                pip install -r requirements.txt        # Install dependencies
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh '''
                . venv/bin/activate  # Activate virtual environment before running tests
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
    }
}
