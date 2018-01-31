pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('build') {
            steps {
            sh 'echo "test" > generate.html'
            sh 'echo "DONE"'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'generate.html', fingerprint: true
        }
    }
}
