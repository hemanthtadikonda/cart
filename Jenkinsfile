pipeline {
    agent any

    stages {
        stage('compile code') {
            steps {
                //sh 'npm install'
                echo 'Hello World'
            }
        }
        stage('test') {
            steps {
                // sh 'npm test'
                echo 'Hello World'
            }
        }
        stage('code quality') {
            steps {
                // sh 'sonar qube command'
                echo 'Hello World'
            }
        }
        stage('code security') {
            steps {
                echo 'we go there'
            }
        }
        stage('Release') {
            steps {
                when {
                    expression { env.TAG_NAME ==~ ".*" }
                }
                echo 'Hello World'
            }
        }
    }
}