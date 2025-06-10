pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR-USERNAME/YOUR-REPO.git'
            }
        }
        
        stage('Setup Python') {
            steps {
                sh 'python --version'
                sh 'pip --version'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'pytest tests/ --cov=calculator --cov-report=xml'
            }
            post {
                always {
                    junit '**/test-reports/*.xml'
                    cobertura coberturaReportFile: '**/coverage.xml'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed'
        }
    }
}
