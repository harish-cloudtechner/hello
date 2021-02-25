pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main',
                credentialsId: 'a8c03966-bbf7-4e70-95b4-cee17a8a639f',
                url: 'https://github.com/hsct2707/hello.git'
                }
        }
        stage ('Compile') {
            steps {
                sh 'mvn compile'
                }
            }  
        stage('Test') {
            steps {
                sh 'mvn test'
            }
           
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
       stage ('Create war file') {
                steps {
                    sh 'jar -cf target/dependency/webapp-runner.jar target/my-app-1.0-SNAPSHOT.jar'
                    }
                }
          
         stage ('Deploy War File') {
                 steps {
                   sh "cp target/my-app-1.0-SNAPSHOT.jar /home/ec2-user/apache-tomcat-8.5.61/webapps"
                    }
                }
    }
}
