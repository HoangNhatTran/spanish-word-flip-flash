pipeline {
    agent {
        docker {
            image 'node:22-alpine'
            // Nhớ thêm các tham số này để không bị lỗi Docker API như lúc trước
            args '-v /var/run/docker.sock:/var/run/docker.sock -e DOCKER_HOST=unix:///var/run/docker.sock'
        }
    }

    stages {
        stage('build') {
            steps {
                sh 'npm ci'
                sh 'npm run build'
            }
        }

        stage('unit tests') {
            steps {
                // Giờ đây nó sẽ tìm thấy vitest vì node_modules vẫn còn đó
                sh 'npm run test' 
            }
        }

        stage('deploy') {
            steps {
                echo 'Mock deployment successful!'
            }
        }
    }
}