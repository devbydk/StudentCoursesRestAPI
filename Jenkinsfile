pipeline {
    agent { label 'JDK_17'}
    triggers {
        pollscm('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/khajadevopsmarch23/StudentCoursesRestAPI'
                    branch: 'develop'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t devbydk/spc:latest .'
            }

        }
        stage('scan') {
            steps {
                sh 'echo docker scan devbydk/spc:latest'
                sh 'docker image push devbydk/spc:latest'
            }
        }
    }

}