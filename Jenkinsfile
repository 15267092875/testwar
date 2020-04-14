pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'choose env'
                input "Does this environment look ok?"
                echo 'Building'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                input "Are you sure deploy?"
            }
        }
    }
}
