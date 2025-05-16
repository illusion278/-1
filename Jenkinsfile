pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat '''
                cd C:\\ProgramData\\Jenkins\\workspace\\jamesreturn27
                if not exist build mkdir build
                cd build
                "C:\\Program Files\\CMake\\bin\\cmake.exe" "C:\\ProgramData\\Jenkins\\workspace\\jamesreturn27"
                "C:\\Program Files\\CMake\\bin\\cmake.exe" --build . --config Release
                '''
            }
        }
    }
}