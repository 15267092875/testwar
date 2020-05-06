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
                        hello()
                        tool.PrintMe('this is my sharelib!')
                    }
                    echo "[BUILD_ID]           : ${env.BUILD_ID}"
                echo "[BUILD_NUMBER]       : ${env.BUILD_NUMBER}"
                echo "[BUILD_DISPLAY_NAME] : ${env.BUILD_DISPLAY_NAME}"
                echo "[JOB_NAME]           : ${env.JOB_NAME}"
                echo "[JOB_BASE_NAME]      : ${env.JOB_BASE_NAME}"
                echo "[BUILD_TAG]          : ${env.BUILD_TAG}"
                echo "[EXECUTOR_NUMBER]    : ${env.EXECUTOR_NUMBER}"
                echo "[NODE_NAME]          : ${env.NODE_NAME}"
                echo "[NODE_LABELS]        : ${env.NODE_LABELS}"
                echo "[WORKSPACE]          : ${env.WORKSPACE}"
                echo "[JENKINS_HOME]       : ${env.JENKINS_HOME}"
                echo "[JENKINS_URL]        : ${env.JENKINS_URL}"
                echo "[BUILD_URL]          : ${env.BUILD_URL}"
                echo "[JOB_URL]            : ${env.JOB_URL}"
                echo "[GIT_COMMIT]         : ${env.GIT_COMMIT}"
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
