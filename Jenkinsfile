pipeline {
    agent any

    tools {
        gradle 'gradle'
    }


   
    stages {
        stage('Clone repository') {
            steps {
                echo 'Cloning repository'
                git branch: 'master', url: 'https://github.com/Raddames-Tonui/java-todo.git'
            }
        }
        stage('Build ') {
            steps {
                echo "Build number ${BUILD_NUMBER}"
                // withGradle() {
                    sh 'gradle build'
                // }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the project in jenkins'
                // withGradle() {
                    sh 'gradle test'
                // }
            }
        }
    }
    post {
        success {
            slackSend color: "good", message: "Build #${BUILD_NUMBER} ran successfully"
        }
        
        failure {
            slackSend color: "danger", message: "Build #${BUILD_NUMBER} failed"
        }
    }
}
