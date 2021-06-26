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
                sh 'cp target/*.jar /var/jenkins_home'
                sh 'java -jar /var/jenkins_home/my-app-1.0-SNAPSHOT.jar > /var/jenkins_home/2.txt'
                sh 'cat /var/jenkins_home/2.txt'

            }
        }

    }
    
}
