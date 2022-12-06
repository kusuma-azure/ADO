pipeline {
    agent { label '' }
    

    environment {
        JAVA_HOME = "${jdk}"
    }

    stages {
        stage('Prepare') {
            
            steps {
                checkout scm
            }
        }

        stage('Test') {
            
            steps {

                sh 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/ && mvn install'
            }
        }

        stage('QA') {
            
            steps {
                
                        echo "test"
                   
               
            }
        }
    }
}
