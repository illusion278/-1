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
                bat """
                if not exist build mkdir build
                cd build
                "C:\\Program Files\\CMake\\bin\\cmake.exe" ..
                "C:\\Program Files\\CMake\\bin\\cmake.exe" --build . --config Release
                """
            }
        }
    }
}