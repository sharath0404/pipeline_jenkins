pipeline {
    agent none
    stages {
        stage('STAGE1'){
            agent {
                label 'slave2'
            }
            steps {
                ansiColor('xterm') {
                sleep 10
                echo "This is stage 1"
            }
        }
        }
        stage('STAGE2') {
            agent {
                label 'slave1'
            }
            steps {
                sleep 10
                echo "This is stage 2"
            }
        }
    }
}
