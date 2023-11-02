pipeline {
    agent any
    stages {
        stage ("test") {
            steps {
                script {
                    echo "Testing the application"
                    echo "Executing pipeline for branch  $BRANCH_NAME"
                }
            }
        }


        stage ("build") {
                when {
                    expression {
                        BRANCH_NAME == "jenkins-jobs"
                    }
                }
            steps {
                script {
                    echo "Building the application"
                }
            }
        }


        stage ("deploy") {
            when {
                    expression {
                        BRANCH_NAME == "jenkins-jobs"
                    }
                }
            steps {
                script {
                    echo "deploy the application"
                }
            }
        }
    }

}








