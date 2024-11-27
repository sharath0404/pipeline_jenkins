pipeline {
    agent none
    stages {
        stage('STAGE1'){
            agent slave2
            steps {
                sleep 10
                echo "This is stage 1"
            }
        }
        stage('STAGE2') {
            agent slave1
            steps {
                sleep 10
                echo "This is stage 2"
            }
        }
    }
}
