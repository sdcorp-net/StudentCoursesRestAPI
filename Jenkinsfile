pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/sdcorp-net/StudentCoursesRestAPI.git',
                    branch: 'develop'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t surajd16/spc:latest .'
            }
        }
        stage('scan and push') {
            steps {
                sh 'echo docker scan surajd16/spc:latest'
                sh 'docker image push surajd16/spc:latest'
            }
        }
    }

}