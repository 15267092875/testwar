pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                
                echo 'choose env'
                input "Does this environment look ok?"
                echo 'Building'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/15267092875/druid.git']]])
                sh label: '', script: 'pwd && ls'
                
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
