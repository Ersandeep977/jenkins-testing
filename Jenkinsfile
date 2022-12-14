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
                git ' https://github.com/Ersandeep977/DevOps-FunctionTesting-code.git'
            }
        }
        stage('Function_Testing') {
            steps {
                sh 'java -jar /var/lib/jenkins/workspace/pipeline-1/testing.jar'
            }
        }
        // stage('Dockerfile_Design')
        // {
        //     steps
        //     {
        //         sh '''cat >Dockerfile<<EOF
        //             FROM tomee 
        //             MAINTAINER sandeep
        //             COPY  webapp /var/lib/jenkins/workspace/pipeline-1/webapp/target/webapp.war
        //         EOF'''    
        //     }
        // }    
    }
}
