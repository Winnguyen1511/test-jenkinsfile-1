pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir('/var/jenkins_home/workspace/5_test-pipeline-1_master') {
                    git 'https://github.com/Winnguyen1511/test-jenkinsfile-1'
                    sh 'cp index.html index-testsh.html'
                    checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/'+params.BRANCH]], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Winnguyen1511/test-jenkinsfile-1']]]
                }
            }
        }
    }
}