pipeline {
    agent any
    tools {
        nodejs 'yarn'
    }

    stages {
        stage('checkout and install') {
            git branch: 'main', url: 'https://github.com/LorenzoTNG/ciCdPlayground'
            sh 'yarn'
            sh 'yarn build'
        }

        stage('unit test') {
            steps {
                sh 'yarn test'
            }

            post {
                always {
                    junit '**/reports/**/*.xml'
                }
            }
        }

        stage('e2e') {
            steps {
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
