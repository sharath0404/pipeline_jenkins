pipeline {
    agent none
    ansiColor('xterm'){

    }
    stages {
        stage('STAGE1'){
            agent {
                label 'slave2'
            }
            steps {
                ansiColor('xterm') {
                sh sleep 10
                echo "This is stage 1"
            }
        }
        }
        stage('STAGE2') {
            agent {
                label 'slave1'
            }
            steps {
                sh sleep 10
                echo "This is stage 2"
            }
        }
    }
}
