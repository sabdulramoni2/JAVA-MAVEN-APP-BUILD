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
                    echo "building the docker image....."
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                             sh 'docker build -t ashiwaju/jupiter12:jma-5.0 .'
                             sh 'echo $PASS | docker login -u $USER --password-stdin'   
                             sh 'docker push ashiwaju/jupiter12:jma-5.0'
                    }
                }
            }
        }

        stage ("testing") {
            steps {
                script {
                    echo 'testing the app'
                }
            }
        }

        stage ("deploy") {
            steps {
                script {
                    echo 'deploying the app'
                }
            }
        }
    }

}







