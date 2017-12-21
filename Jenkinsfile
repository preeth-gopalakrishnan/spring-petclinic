pipeline {
    agent {
   		label 'linux'     
    }
    stages {
        stage('Build') {
            agent { 
	            docker {
	            image 'maven:3.5-alpine' 
	            label 'linux'
	            }
            }
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('Deploy') {
          steps {
            input 'Do you approve the deployment?'
            sh 'echo deploying....'
          }
        }
    }
}
