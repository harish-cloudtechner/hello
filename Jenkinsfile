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
stage ('Clean') {
steps {
sh 'mvn clean'
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
post {
always {
junit '**/target/surefire-reports/*.xml'
}
}
}
stage ('Package') {
steps {
sh 'mvn package'
}
}
stage ('Deploy War File') {
steps {
sh "cp /root/.jenkins/workspace/junit/gameoflife-web/target/gameoflife.war /home/ec2-user/apache-tomcat-8.5.61/webapps/"
}
}
}
}
