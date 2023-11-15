pipeline {
	agent any

	stages{
	  stage("Git Checkout"){
		steps{
		git branch: 'main', url: 'https://github.com/devopsncloud/CounterApp.git'

	}		
}


 stage("Unit Testing "){
                steps{
			sh 'mvn test'
        }
      }

stage("Integration Testing "){
                steps{
                        sh 'mvn verify -DskipUnitTests'
        }
      }

	stage("Build stage"){

		steps{
			sh 'mvn clean install'
}
}

stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'jenkinssonar') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                   }
                    
                }
            }

    }
 }
