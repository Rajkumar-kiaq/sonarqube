pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Rajkumar-kiaq/sonarqube.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script{
                    
                    def scannerHome = tool 'sonarscanner'
                    withSonarQubeEnv('SonarQube') {
                        sh """
                            ${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=sonarqube-raj \
                            -Dsonar.projectName=sonarqube-raj \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://localhost:9000 \
                            -Dsonar.login=sqp_23d9655d28c3c5de7418b35556806dd76e6f9839
                        """
                    }
                }
            }
        }
    }
}
