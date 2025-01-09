pipeline {
    agent any
    tools {
        maven 'maven3'
        jdk 'java17'
    }
    stages {
        stage('Download Code From Git') {
            steps {
                git branch: 'main', url: 'https://github.com/devopstechlab/maven-jenkins6.git'
            }
        }
        stage('Build Java Project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive Artifcats') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Trigger Deploy Job') {
            steps {
                build wait: false, job: 'deploy-dev-pipeline'
            }
        }
    }
}