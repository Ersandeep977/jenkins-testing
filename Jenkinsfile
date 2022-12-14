pipeline {
    agent any
    stages {
        stage('Git_Code_Downloding') {
            steps {
                script
                {
                   try
                   {
                       git 'https://github.com/Ersandeep977/DevOps-Maven-code.git'
                       echo 'Git Code Downloding .....DON'
                   }
                   catch(Exception e1)
                   {
                     echo "Git Downloading Not woring plz check..."
                     exit(1)
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
                    echo 'MVN Package .....DON'
                   }
                   catch(Exception e2)
                   {
                     echo "MVN Packges Not woring plz check..."
                     exit(1)
                   }
                }
            }
        }
        stage('Functional_testing_code_Downdoling') {
            steps {
                script
                {
                   try
                   {
                    git 'https://github.com/Ersandeep977/DevOps-FunctionTesting-code.git'
                   echo 'Functional testing Code Downloding .....DON'
                   }
                   catch(Exception e3)
                   {
                     echo "Functional testing code Not Download plz check..."
                     exit(1)
                   }
                }
            }
        }
        stage('Code_Testing') {
            steps {
                script
                {
                   try
                   {
                    sh 'java -jar testing.jar'
                    echo 'Code Testing .....DON'
                   }
                   catch(Exception e4)
                   {
                     echo "Functional testing Not woring plz check..."
                     exit(1)
                   }
                }
            }
        }
        stage('Dockerfile_Cration') {
            steps {
                script
                {
                   try
                   {
                    sh '''
                    cat >Dockerfile<<EOF
                    FROM tomee 
                    MAINTAINER Sandeep
                    COPY  webapp /usr/local/tomee/webapps/testapp.war
                    '''
                    echo 'Dockerfile Cration .....DON'
                   }
                   catch(Exception e5)
                   {
                     echo "Dockerfile Cration Not woring plz check..."
                     exit(1)
                   }
                }
            }
        }
        stage('Docker_Images_Images_cration') {
            steps {
                script
                {
                   try
                   {
                    sh 'sudo docker build -t patel977/java-aap:v1 .'
                    echo 'Docker Images Images cration.....DON'
                   }
                   catch(Exception e6)
                   {
                     echo "Docker Images Images cration Not woring plz check..."
                     exit(1)
                   }
                }
            }
        }
        stage('Docker_Images_Push_Hub') {
            steps {
                script
                {
                   try
                   {
                    sh 'sudo docker push patel977/java-aap:v1'
                    echo 'Docker Images Push Hub cration.....DON'
                   }
                   catch(Exception e7)
                   {
                     echo "Docker Images Push Hub Not woring plz check..."
                     exit(1)
                   }
                }
            }
        }
    }
     post {
        always {
            echo "This block always runing....."
        }
        aborted {
            echo "build process is aborted.....................OK"
        }
        failure {
            echo "build is failed..............OK"
        }
        success {
            echo "build is succeeded........OK"
        }
        unsuccessful {
            echo "This block runs when the current status is anything except success."
        }
        unstable {
            echo "This block runs if the current status is marked unstable."
        }
        changed {
            echo "This block runs when the current status is different than the previous one."
        }
     }
}