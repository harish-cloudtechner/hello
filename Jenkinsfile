pipeline {
agent any
tools {
maven 'maven'
}
stages {
stage('Git Checkout') {
steps {
git branch: 'main',
credentialsId: '91fc54de-d013-4007-9e77-eb2fb97161a8',
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
junit '**/target/surefire/*.xml'
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
sh "cp /root/.jenkins/workspace/junit/gameoflife-web/target/gameoflife.war /home/ubuntu/apache-tomcat-8.5.61/webapps/"
}
}
}
}
