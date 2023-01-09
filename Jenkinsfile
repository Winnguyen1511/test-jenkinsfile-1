pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Winnguyen1511/test-jenkinsfile-1'
                sh 'cp index.html index-testsh.html'
            }
        }
    }
}