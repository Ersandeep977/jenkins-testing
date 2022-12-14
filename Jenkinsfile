pipeline {
    agent any
    stages {
        stage('Git_Code_Downloding') {
            steps {
                git 'https://github.com/Ersandeep977/DevOps-Maven-code.git'
            }
        }
        stage('Build_java_Code') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Function_Testing_Code_Downlod') {
            steps {
              //  git ' https://github.com/Ersandeep977/DevOps-FunctionTesting-code.git'
            }
        }
        stage('DockerFile_Cration') {
            steps {
                sh '''
                cat >dockerfile<<EOF
                    FROM tomee 
                    MAINTAINER intelliqit
                    COPY  webapp /var/lib/jenkins/workspace/pipleine-1/webapp/target/testapp.war
                EOF
                '''
            }
        }    
    }
}
