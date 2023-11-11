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
                
                    withSonarQubeEnv( 'sonar') {
                        sh '''$scannerHome/bin/sonar-scanner \
                        -Dsonar.projectKey=sonarqube \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.java.binaries=. \
                        -Dsonar.projecKey=sonarqube '''
                    }
                }
                
            
        }
       
       

}
}

