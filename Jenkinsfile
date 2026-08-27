pipeline {
    agent { label 'svr1-akmal' }

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/studyakmal/simple-apps.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    cd apps
                    npm install
                '''
            }
        }

        stage('Testing') {
            steps {
                sh '''
                    cd apps
                    npm test
                    npm run test:coverage
                '''
            }
        }

        stage('Code Review') {
            steps {
                sh '''
                    cd apps
                    sonar-scanner \
                        -Dsonar.projectKey=simple-apps \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://172.23.8.116:9000 \
                        -Dsonar.token=sqp_628301705fdc4945064d76917947b8866c14fbc3
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker compose up --build -d
                '''
            }
        }
    }
}