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
            sh 'echo "Report1" > report1.html'
            sh 'echo "(Report1 temp)" > report1.tmp'
            sh 'echo "Report2" > build/report2.html'
            sh 'echo "Report3" > build/gendir/report3.html'
            sh 'echo "Temp1" > temp1.html'
            sh 'echo "Temp2" > build/temp2.html'
            sh 'echo "Temp3" > build/gendir/temp3.html'
            sh 'echo "DONE"'
            }
        }
    }

    post {
        always {
            sh 'ls -l'
            sh 'ls build -l'
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
