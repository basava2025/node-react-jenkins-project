pipeline {
    agent any

    environment {
        CI = 'true'
    }

    stages {

        stage('Build') {
            steps {
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }

        stage('Deliver') {
            steps {
                echo "Starting application..."

                // Run app (example)
                bat 'npm start'

                input message: 'Finished using the web site? Click Proceed to stop'

                echo "Stopping application..."

                // Kill process (Windows way)
                bat 'taskkill /F /IM node.exe || exit 0'
            }
        }
    }
}