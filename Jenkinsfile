pipeline {
    agent any
    stages {
        stage('Git_Code_Downloding') {
            steps {
                git 'https://github.com/Ersandeep977/DevOps-Maven-code.git'
            }
        }
        stage('Code_Building') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Functional_testing_code_Downdoling') {
            steps {
                git 'https://github.com/Ersandeep977/DevOps-FunctionTesting-code.git'
            }
        }
        stage('Code_Testing') {
            steps {
                sh 'java -jar testing.jar'
            }
        }
        stage('Dockerfile_Cration') {
            steps {
                sh '''
                cat >dockerfile<<EOF
                    FROM tomee 
                    MAINTAINER Sandeep
                    COPY  webapp /usr/local/tomee/webapps/testapp.war
                '''
            }
        }
    }
}
