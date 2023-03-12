pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* 23 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/sdcorp-net/StudentCoursesRestAPI.git',
                    branch: 'sprint_1_release'
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