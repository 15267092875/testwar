#!groovy

@Library('sharelib')

def tool = new org.opsdev.print()

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                timeout(time:30,unit:'MINUTES'){
                    script(){
                        println("ceshi sharelib")
                        tool.PrintMe('this is my sharelib!')
                    }
                }
                echo 'choose env'
                input "Does this environment look ok?"
                echo 'Building'
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/15267092875/druid.git']]])
                sh label: '', script: '/app/apache-maven-3.6.3/bin/mvn clean package'
                
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
