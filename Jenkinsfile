pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/tejastudent/jenkins.git'
            }
        }
        stage('Display HTML') {
            steps {
                // Display the contents of index.html
                script {
                    if (fileExists('first.html')) {
                        echo "HTML File Contents:"
                        sh 'cat first.html'
                    } else {
                        echo "first.html file not found."
                    }
                }
            }
        }
        stage('Publish HTML Report') {
            steps {
                // Archive and publish HTML report (requires HTML Publisher Plugin)
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: '.',
                    reportFiles: 'first.html',
                    reportName: 'HTML Report'
                ])
            }
        }
    }
}