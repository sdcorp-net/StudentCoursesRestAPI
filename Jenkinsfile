pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* 23 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/khajadevopsmarch23/StudentCoursesRestAPI',
                    branch: 'sprint_1_release'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t shaikkhajaibrahim/spc:latest .'
            }
        }
        stage('scan and push') {
            steps {
                sh 'echo docker scan shaikkhajaibrahim/spc:latest'
                sh 'docker image push shaikkhajaibrahim/spc:latest'
            }
        }
    }

}