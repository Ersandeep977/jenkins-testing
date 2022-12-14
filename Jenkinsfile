pipeline {
    agent any
    stages {
        stage('Git_Code_Downloding') {
            steps {
                script
                {
                   try
                   {
                       git 'https://github.com/Ersandeep977/DevOpsssss-Maven-code.git'
                   }
                   catch(Exception e1)
                   {
                     echo "Git Downloading Not woring plz check..."
                   }
                }
            }
        }
        stage('Code_Building') {
            steps {
                script
                {
                   try
                   {
                    sh 'mvn package'
                   }
                   catch(Exception e2)
                   {
                     echo "MVN Packges Not woring plz check..."
                   }
                }
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
                cat >Dockerfile<<EOF
                    FROM tomee 
                    MAINTAINER Sandeep
                    COPY  webapp /usr/local/tomee/webapps/testapp.war
                '''
            }
        }
        stage('Docker_Images_Images_cration') {
            steps {
                sh 'sudo docker build -t patel977/javaap:v1 .'
            }
        }
        stage('Docker_Images_Push_Hub') {
            steps {
                sh 'sudo docker push patel977/javaap:v1'
            }
        }
    }
}
