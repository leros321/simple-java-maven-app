pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
        }
                script {
                    currentBuild.displayName = "The name."
                    currentBuild.description = "The best description."
}
    		post {
       		  success{
        	     archiveArtifacts 'target/*.jar'
    }
  }
}
        stage('Test') { 
            steps {
                sh 'mvn test surefire-report:report' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
}
