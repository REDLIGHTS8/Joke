pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/REDLIGHTS8/Joke.git'
            }
        }
        
        stage('Build') {
            steps {
                sh '''
                    mkdir -p build
                    cd build
                    cmake ..
                    make
                '''
            }
        }
        
        stage('Test') {
            steps {
                sh 'cd build && ctest --output-on-failure'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
