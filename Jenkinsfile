pipeline {
    agent any
    stages {
        stage('Print env vars') {
            steps { 
                sh 'env > env.txt' 
                for (String i : readFile('env.txt').split("\r?\n")) {
                    println i
                }
                sh 'printenv'
            }
        }
    }
}