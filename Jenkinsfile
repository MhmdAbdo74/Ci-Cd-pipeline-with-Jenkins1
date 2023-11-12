pipeline{
    
    agent any 
    environment{
        
        SCAANER_HOME = tool 'sonar'
    }
    tools{
        
        maven 'maven'
      
    }
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/MhmdAbdo74/Ci-Cd-pipeline-with-Jenkins1.git'
                }
            }
        }
        stage('Unit Test'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration Test'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipunitTests'
                }
            }
        }
        stage('Build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('sonarqube analysis')
        {
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar') {
                        sh 'mvn clean package  sonar:sonar'
                    }
                }
                
            
        }
       
       

}
    stage('quality gate'){
        steps{
             script{
                
            waitForQualityGate abortPipeline: false, credentialsId: 'sonar'
             }
            }
        }

        stage('push artifact to nexus'){
            steps{
                script{
                    def readPomVersion = readMavenPom file: 'pom.xml'
                    def nexusrepo = readPomVersion.version.endsWith("SNAPSHOT") ? "demoapp-snapshot" : "demoapp-release"
                    nexusArtifactUploader artifacts:
                    [
                        
                        [
                            artifactId: 'springboot', 
                            classifier: '',
                            file: 'target/Uber.jar',
                            type: 'jar'
                        ]
                    ],
                            credentialsId: 'nexus-cred',
                            groupId: 'com.example',
                            nexusUrl: '54.234.198.96:8081',
                            nexusVersion: 'nexus3',
                            protocol: 'http',
                            repository: "${nexusrepo}",
                            version: "${readPomVersion.version}"
                }
            }
        }
        stage('Docker image build'){
            steps{
                script{
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
               

                }
            }
        }
    }
}
