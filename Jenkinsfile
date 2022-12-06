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

                sh 'mvn verify package'
            }
        }

        stage('Unit Test') {
            
            steps {
                
                       sh 'mvn test'
                   
               
            }
        }
    }
}
