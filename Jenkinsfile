#!/user/bin/env groovy

def gv

pipeline {
    agent any 
    tools {
        maven 'maven-3.9'
    }


         stage ("build app") {
            steps {
                script {
                    echo 'building the application..'
                    sh 'mvn package'
                }
            }
        }

        stage ("build image") {
            steps {
                script {
                   gv.buildImage()
                }
            }
        }

        stage ("testing") {
            steps {
                script {
                    gv.testApp()
                }
            }
        }

        stage ("deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }

}







