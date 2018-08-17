pipeline {
    agent {
        label '!windows'
    }
    options {
        timeout(time: 4, unit: 'HOURS')
        timestamps()
        buildDiscarder(logRotator(artifactDaysToKeepStr: '2', artifactNumToKeepStr: '5', daysToKeepStr: '15', numToKeepStr: '15'))
    }
    triggers {
        pollSCM('H/2 * * * *')
    }
    tools {
      ant 'ant-latest'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout(poll: true,
                         scm: [$class: 'GitSCM',
                               branches: [[name: 'refs/heads/JENKINS-52746']],
                               extensions: [
                                            [$class: 'CloneOption', honorRefspec: true, noTags: true, reference: '/var/lib/git/mwaite/bare/bugs/jenkins-bugs.git'],
                                            [$class: 'AuthorInChangelog'],
                                            [$class: 'LocalBranch', localBranch: 'JENKINS-52746'],
                                           ],
                               gitTool: scm.gitTool,
                               userRemoteConfigs: [[refspec: '+refs/heads/JENKINS-52746:refs/remotes/origin/JENKINS-52746', url: 'git://wheezy64b.markwaite.net/mwaite/bugs/jenkins-bugs.git']]])
            }
        }
        stage('Test and Package') {
            steps {
                sh 'ant info'
            }
        }
    }
    // post {
    //     always {
    //         /* Confirmed that if deleteDir is there, then multibranch pipeline will build the branch on every poll. */
    //         deleteDir()
    //     }
    // }
}
