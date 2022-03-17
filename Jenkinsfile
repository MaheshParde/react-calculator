pipeline {
    
	  agent any
  tools {nodejs "node"}

	environment{
	registry="maheshparde/rect-test"
	registryCredential='dockerhub'
	dockerImage=''
	}
    
    //def registry = 'mrchelsea/testing-docker'
    //def registryCredential = 'dockerhub'
	stages{
	stage('Git') {
		steps{
		git 'https://github.com/MaheshParde/react-calculator.git'
		}	
	}
	stage('Build') {
		steps{
		sh 'yarn'
		}	
	}
	/*stage('Test') {
		steps{
		sh 'npm test'
		}
	}*/
	stage('Building image') {
		steps{
			script{
			 	sh "docker build -t maheshparde/rect-test ."	
			}
		}
	}
	stage('Registring image') {
		steps{
			script{
				docker.withRegistry('',registryCredential){
				sh "docker push maheshparde/rect-test"
				}
			}
		}
	}
	}
	
}	
    
