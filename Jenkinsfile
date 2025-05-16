pipeline {
    agent any  // Запуск на любом доступном агенте
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Клонирование репозитория
            }
        }
        stage('Build') {
            steps {
                sh '''
                mkdir -p build
                cd build
                cmake .. && make
                '''
            }
        }
        stage('Test') {  // Опционально
            steps {
                sh 'cd build && ctest --output-on-failure'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**/*'  // Сохранение артефактов
        }
    }
}