pipeline {
    agent {
        node {
            label 'linux-build-slave-test'
        }
    }
    stages {
        stage('Build') {
            steps {
                dir('/var/jenkins_home/workspace/'+ env.BUILD_NUMBER + '_'+params.PROJECT+'_'+params.BRANCH) {
                    git 'https://github.com/Winnguyen1511/test-jenkinsfile-1'
                    sh 'cp index.html index-testsh.html'
                    checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/'+params.BRANCH]], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Winnguyen1511/test-jenkinsfile-1']]]
                }
            }
        }
    }
}