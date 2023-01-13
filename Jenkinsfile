pipeline {
    agent any
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
                sshPublisher(publishers: [sshPublisherDesc(configName: 'linux-jenkins-slave-1', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: env.BUILD_NUMBER+'_'+params.PROJECT+'_'+params.BRANCH, remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}