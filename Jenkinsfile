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
    checkout([
    $class: 'GitSCM',
    branches: [[name: '*/master']],
    extensions: [],
    userRemoteConfigs: [[
        credentialsId: '6d1e6e16-e0e1-4661-aa98-bde11f19505b',
        url: 'https://github.com/REDLIGHTS8/Joke.git'
    ]]
])
}
