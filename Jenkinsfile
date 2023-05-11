pipeline {
    agent { label 'JDK_17'}
    triggers {
        pollSCM('35 11 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/devbydk/StudentCoursesRestAPI.git',
                    branch: 'sprint_1_release'
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
