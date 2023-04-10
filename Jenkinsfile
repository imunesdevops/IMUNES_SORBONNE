pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install tcl'
                sh 'sudo apt-get install tcllib'
            }
        }
        stage('Run tests') {
            steps {
                sh '''
                    package require tcltest

                    # Définit un ensemble de tests nommé "mon_test"
                    namespace eval mon_test {
                        # Définit un test nommé "test_true" qui renvoie toujours "true"
                        proc test_true {} {
                            set x 1
                            set y 1
                            set result [expr {$x == $y}]
                            tcltest::assert $result
                        }
                    }

                    # Exécute l'ensemble de tests "mon_test"
                    tcltest::runTests mon_test
                '''
            }
        }
    }
}
