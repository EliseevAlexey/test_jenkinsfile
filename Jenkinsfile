#!groovy

properties([disableConcurrentBuilds()])

pipeline {
    agent {
        label 'master'
    }
    triggers { pollSCM('* * * * *') }
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
    }
    
    stages {
        stage ("Create docker image") {
            steps {
                echo "====== start build image ====="
                sh 'docker build -t toolbox:latest .'
            }
        }
    }
}
