pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate Website') {
            steps {
                sh '''
                    test -f index.html
                    test -f calculator.html
                    test -f calendar.html
                    test -f digitalclock.html
                    test -f notesapp.html
                    test -f todo.html
                    test -f Dockerfile


                    echo "All HTML application files found!"
                '''
            }
        }

         stage('Build Docker Image') {
            steps {
                sh 'docker build -t web-hub-tool:latest .'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                    docker rm -f web-hub-tool || true
                    docker run -d \
                        --name web-hub-tool \
                        --restart unless-stopped \
                        -p 8081:80 \
                        web-hub-tool:latest
                '''
            }
        }
    }
}
