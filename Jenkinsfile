pipeline {

    agent {
        node {
            label 'master'
        }
    }

    tools { 
        maven 'maven3' 
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '15', 
                    numToKeepStr: '10'
            )
    }

    environment {
        APP_NAME = "STUDENT_APP"
        APP_ENV  = "DEV"
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace for ${APP_NAME}"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }

        stage('Code Build') {
            steps {
               //  sh 'mvn install -Dmaven.test.skip=true'
                 echo "Code Build"
            }
        }
   
        stage('Enviroment Analysis') {
            parallel {
              
                 stage('task 1') {
                     steps {
              
                               echo "task 1"
                      }
                   }
                    stage('task 2') {
                     steps {
              
                               echo "task 2"
                      }
                      }
                    stage('task 3') {
                     steps {
              
                               echo "task 3"
                      }
                 }
                  
   
                
                
            }
        }
        
        
        stage('Printing All Global Variables') {
            steps {
                sh """
                env
                """
            }
        }

    }   
}
