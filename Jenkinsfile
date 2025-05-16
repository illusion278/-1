pipeline {
    agent any  // Запуск на любом доступном агенте (включая Windows)
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Клонирование репозитория (работает на всех ОС)
            }
        }
        stage('Build') {
            steps {
                bat '''  // Заменяем sh на bat для Windows
                if not exist build mkdir build
                cd build
                cmake .. && cmake --build . --config Release
                '''
            }
        }
        stage('Test') {  // Опционально
            steps {
                bat '''  // Заменяем sh на bat
                cd build
                ctest --output-on-failure
                '''
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**/*'  // Сохранение артефактов
        }
    }
}