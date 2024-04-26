pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/lukaszszczot/SimpleProgram.git'
            }
        }
        stage('Build with Maven') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Run program') {
            steps {
                bat 'java -cp target/classes org.example.Main'
            }
        }
    }
}