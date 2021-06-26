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
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('deploy') {
            steps {
                sh 'cp target/*.jar /root'
                sh 'java -jar /root/my-app-1.0-SNAPSHOT.jar > /root/2.txt'
                sh 'cat /root/2.txt'

            }
        }

    }
    
}
