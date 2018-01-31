pipeline {
    agent { docker 'maven:3.3.3' }
    stages {

        stage('cleanup') {
            steps {
                deleteDir()
            }
        }

        stage('build') {
            steps {
            sh 'mkdir -p build/gendir'
            sh 'echo "Report 1" > report 1.html'
            sh 'echo "(Report 1 temp)" > report 1.tmp'
            sh 'echo "Report 2" > build/report 2.html'
            sh 'echo "Report 3" > build/gendir/report 3.html'
            sh 'echo "Temp 1" > temp 1.html'
            sh 'echo "Temp 2" > build/temp 2.html'
            sh 'echo "Temp 3" > build/gendir/temp 3.html'
            sh 'echo "DONE"'
            sh 'ls'
            }
        }
    }

    post {
        always {
            sh 'ls -l'
            archiveArtifacts artifacts: '**/*.html', fingerprint: true
            sh 'pwd'
            sh 'pwd && cd build'
            archiveArtifacts artifacts: '**/*.html', fingerprint: true
            sh 'ls -l'
            sh 'cd build/gendir'
            archiveArtifacts artifacts: '**/*.html', fingerprint: true

        }
    }
}
