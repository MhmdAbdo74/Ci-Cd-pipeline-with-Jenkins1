pipeline{
    
    agent any 
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
                    
                    sh 'mvn clean package'
                }
            }
        
        }
        stage('static code analysis'){
            
            steps{
                    
                    script{
                
               withSonarQubeEnv(credentialsId: 'sonar-api') {
            // some block
            sh 'mvn clean package sonar:sonar'
           }
                }
            }
        }

}



