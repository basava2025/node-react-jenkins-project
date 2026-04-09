pipeline {
    agent any

    parameters {
        extendedChoice(
            name: 'COMPONENTS',
            type: 'PT_CHECKBOX',
            value: 'frontend,backend,database',
            description: 'Select components to deploy'
        )
    }

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
                bat 'npm run build'
            }
        }

        stage('Deploy Selected Components') {
            steps {
                script {
                    def selected = params.COMPONENTS.split(',')

                    if (selected.contains('frontend')) {
                        echo "Deploying Frontend"
                    }
                    if (selected.contains('backend')) {
                        echo "Deploying Backend"
                    }
                    if (selected.contains('database')) {
                        echo "Deploying Database"
                    }
                }
            }
        }
    }
}