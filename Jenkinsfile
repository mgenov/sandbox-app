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
            when { tag "service*/**" }
            steps {
                script {
                    // Parse service from Tag in format: service1/1.0.0 common/www-service/1.0.0
                    def service = service("${GIT_BRANCH}")
                    echo "Deploying ${service.name} ${service.version}"
                    sh 'echo deploy'
                }
            }
        }       
    }
}

def service(String tag = '') {
    def parts = tag.split('/')
    def ver = parts.last()
    def name = parts[-2]    
    return [name: name,version: ver]
}