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
                    test -f style.css -o -f styles.css
                    test -f script.js -o -f app.js
                    echo "Website files found successfully!"
                '''
            }
        }

        stage('Build Complete') {
            steps {
                echo 'HTML, CSS and JavaScript project is ready!'
            }
        }
    }
}
