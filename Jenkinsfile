pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                
                echo 'choose env'
                input "Does this environment look ok?"
                echo 'Building'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/15267092875/druid.git']]])
                sh label: '', script: 'wget https://mirror.bit.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz && ls'
                sh label: '', script: 'tar -zxvf apache-maven-3.6.3-bin.tar.gz && ./apache-maven-3.6.3/bin/mvn clean package'

                
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
