pipeline {
    agent any
    options {
       // Timeout counter starts AFTER agent is allocated
       timeout(time: 900, unit: 'SECONDS')
       retry(2)
      }
     stages {
	 stage('Source code') {
	   steps {
	      git url: 'https://github.com/Srinath04/spring-petclinic.git',branch: 'main'
	   }
	}			
	 stage('Build the code') {
           steps {
	    sh script: 'mvn clean package'
           }
        }	
        stage('Reporting and Archiving') {
          steps {
	    junit testResults: 'target/surefire-reports/*.xml'
	}	
       }
     }
    post {
	success {
	 //send the success email
	 echo "Success"
    }
	unsuccessful {
	//send the success email
        echo "Failure"
       }
    }
} 
