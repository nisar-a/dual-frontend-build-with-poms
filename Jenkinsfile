pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6' // Replace with your Jenkins Maven tool name
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/nisar-a/dual-frontend-build-with-poms.git' // Replace with your Git repo URL
            }
        }

        stage('Install Dependencies & Build') {
            parallel {
                stage('Build Admin App') {
                    steps {
                        dir('admin') {
                            sh 'mvn clean install'
                        }
                    }
                }

                stage('Build User App') {
                    steps {
                        dir('user') {
                            sh 'mvn clean install'
                        }
                    }
                }
            }
        }
    }

    post {
        success {
            echo '✅ Both Admin and User apps built successfully!'
        }
        failure {
            echo '❌ Build failed. Check the logs.'
        }
    }
}
