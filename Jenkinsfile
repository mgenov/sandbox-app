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

        stage('Deploy Service1') {
            when { tag "service1/*" }
            steps {
                echo 'Deploying service 1 only because this commit is tagged...'
                sh 'echo deploy'
            }
        }

        stage('Deploy Service2') {
            when { tag "service2/*" }
            steps {
                echo 'Deploying service 2 only because this commit is tagged...'
                sh 'echo deploy'
            }
        }
    }
}
