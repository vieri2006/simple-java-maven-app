Node { 
    docker.image('maven:3.9.0').inside {
        stage('Build') { 
            sh 'make' 
        }
        stage('Test') {
            sh 'make check'
            junit 'reports/**/*.xml' 
        }
        if (currentBuild.currentResult == 'SUCCESS') {
            stage('Deploy') {
                sh 'make publish' 
            }
        }
    }
}