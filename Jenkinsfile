pipeline {
    agent any

    stages {
        stage('Update system') {
            steps {
                sh 'sudo apt update'
            }
        }

        stage('Install Apache') {
            steps {
                sh 'sudo apt install -y apache2'
            }
        }

        stage('Check apache2 logs for errors 4xx or 5xx') {
            steps {
                sh '''
                echo "- 4xx errors:"
                grep ' 4[0-9][0-9] ' /var/log/apache2/access.log || echo "No 4xx errors"

                echo "- 5xx errors:"
                grep ' 5[0-9][0-9] ' /var/log/apache2/access.log || echo "No 5xx errors"
                '''
            }
        }
    }
}
