pipeline {
    
    agent any
    
    tools {
        nodejs 'yarn'
    }

    stages {

        stage('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/m-riedl/ciCdPlayground.git'
            }
        }
        
        stage('unit tests') {
            steps {
                sh 'yarn install'
                sh 'yarn test'
            }
                
            post {
                always {
                    junit '**/reports/**/*.xml'
                }
            }
        }
        
        stage('integration tests') {
            steps {
                sh 'yarn build'
                sh 'yarn test:e2e'
                }
                
            post {
                always {
                    junit '**/reports/**/*.xml'
                }
            }
        }
    }    
}    
