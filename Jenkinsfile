pipeline {
    options {
        timestamps()
        skipDefaultCheckout()
    }
    agent {
        label 'windows'
    }
    stages {
        stage('Info') {
            steps {
                git 'https://github.com/amuniz/maven-helloworld'
                // checkout([
                //   $class: 'GitSCM',
                //   branches: scm.branches,
                //   extensions: scm.extensions,
                //   userRemoteConfigs: scm.userRemoteConfigs
                // ])
                // git branch: 'JENKINS-55257', url: 'https://github.com/MarkEWaite/jenkins-bugs'
                // withAnt(installation: 'ant-latest') {
                //     bat 'ant info'
                // }
            }
        }
    }
}
