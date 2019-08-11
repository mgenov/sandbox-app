pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo package'
            }
        }
        stage('Test') {
            steps {
                sh 'echo check'
            }
        }

        stage('Deploy') {
            when { tag "service*/*" }
            steps {
                script {
                    def ver = semver("${GIT_BRANCH}")
                    echo "Deploying version ${ver}"
                    sh 'echo deploy'
                }                
            }
        }       
    }
}

def semver(String tag = '') {
    def version = tag.split('/')[1]
    return version
}