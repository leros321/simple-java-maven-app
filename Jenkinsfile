pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
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
    }
}
