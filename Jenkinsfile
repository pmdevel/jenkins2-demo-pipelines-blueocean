pipeline {
    agent none
    stages {
        stage('Build') {
            steps {
                echo 'Checkout app'
                echo 'Build app'
                echo 'Stash app'
            }
        }

        stage('Test') {
            steps {
                parallel(
                        "linux": {
                            node('java') {
                                echo 'Unstash "binary"'
                                echo 'Testing linux...'
                                sh "sleep 5s"
                                echo 'Testing linux ready!'
                            }

                        },
                        "windows": {
                            node('java') {
                                echo 'Unstash "binary"'
                                echo 'Testing windows...'
                                sh 'sleep 10s'
                                echo 'Testing windows ready!'
                            }
                        }
                )
            }
        }
    }
}