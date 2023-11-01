#!/user/bin/env groovy
Libraryidentifier:'jenkins-shared-Library@master', retriever: modernSCM(
    [$class:'GitSCMSource', 
    remote: 'https://github.com/sabdulramoni2/jenkins-shared-library-final.git', 
    credentialsId: 'git-credentials'])

def gv

pipeline {
    agent any 
    tools {
        maven 'maven-3.9'
    }

    stages {
        stage ("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }

         stage ("build jar") {
            steps {
                script {
                    buildJar()
                }
            }
        }

        stage ("build and push image") {
            steps {
                script {
                   buildImage 'ashiwaju/jupiter12:jma-4.0'
                    dockerLogin()
                    dockerPush 'ashiwaju/jupiter12:jma-4.0'
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







