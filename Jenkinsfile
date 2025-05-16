pipeline {
    agent any
    tools {
        cmake 'CMake'  // Имя инструмента, настроенного в Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
		bat 'cmake --version'
                bat '''
                if not exist build mkdir build
                cd build
                cmake .. 
                cmake --build . --config Release
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                cd build
                ctest --output-on-failure
                '''
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**/*'
        }
    }
}