pipeline {
    agent { label '' }
    

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-11-openjdk-amd64"
        NEXUS_VERSION = "NEXUS3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "13.232.201.1:8081"
        NEXUS_REPOSITORY = "nexus"
        NEXUS_CREDENTIAL_ID = "Nexus"
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
        
        stage("Publish to Nexus Repository Manager") {
            steps {
                script {
                    
                    artifactPath = "target/wicket-pwnedpasswords-validator-2.0.1-SNAPSHOT.jar";
                    artifactExists = fileExists artifactPath;
                    if(artifactExists) {
                        echo "*** File: ${artifactPath}, group: de.martinspielmann.wicket, packaging: jar, version 1.0-SNAPSHOT";
                        nexusArtifactUploader(
                            nexusVersion: NEXUS_VERSION,
                            protocol: NEXUS_PROTOCOL,
                            nexusUrl: NEXUS_URL,
                            groupId: "de.martinspielmann.wicket",
                            version: "1.0-SNAPSHOT",
                            repository: NEXUS_REPOSITORY,
                            credentialsId: NEXUS_CREDENTIAL_ID,
                            artifacts: [
                                [artifactId: "wicket-pwnedpasswords-validator",
                                classifier: '',
                                file: artifactPath,
                                type: "jar"],
                                [artifactId: "wicket-pwnedpasswords-validator",
                                classifier: '',
                                file: "pom.xml",
                                type: "pom"]
                            ]
                        );
                    } else {
                        error "*** File: ${artifactPath}, could not be found";
                    }
                }
            }
         }
     }
        
}
