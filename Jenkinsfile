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

                    echo "All HTML application files found!"
                '''
            }
        }

        stage('Build Complete') {
            steps {
                echo 'Web Hub Tool validation completed successfully!'
            }
        }
    }
}
