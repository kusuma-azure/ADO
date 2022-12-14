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

        stage('Compile') {
            
            steps {

                sh 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 && mvn verify package'
            }
        }

        stage('Unit Test') {
            
            steps {
                
                       sh 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 && mvn test'
                   
               
            }
        }
    }
}
