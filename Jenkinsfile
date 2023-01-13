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
        stage('SSH Publish')
        {
            steps{
                sshagent(['80fba500-0c64-4e32-a936-6462c559c949']) {
                    // sh 'ssh@172.17.0.3'
                    sh 'ssh root@172.17.0.4 "mkdir /root/jenkins_workspace/workspace/'+env.BUILD_NUMBER + '_'+params.PROJECT+'_'+params.BRANCH+'"'
                    sh 'scp -r '+'/var/jenkins_home/workspace/'+ env.BUILD_NUMBER + '_'+params.PROJECT+'_'+params.BRANCH+'/** '+ 'root@172.17.0.4:/root/jenkins_workspace/workspace/'+env.BUILD_NUMBER + '_'+params.PROJECT+'_'+params.BRANCH
                }
            }
        }
    }

}