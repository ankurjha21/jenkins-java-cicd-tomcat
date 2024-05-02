pipeline{
    agent any
    environment {
        TOMCAT_URL = 'http://admin:12345@54.198.233.48:8090/manager/text'
        WAR_FILE = '/var/lib/jenkins/workspace/java-pipeline/target/jb-hello-world-maven-0.2.0.jar'
    }
    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'bbb67623-7c1f-482d-a211-135773d7a017	', url: 'https://github.com/ankurjha21/jenkins-java-cicd-tomcat.git']]])
            }
        }
        stage('build'){
            steps{
               sh 'mvn package'
            }
        }
        stage('Deploy on tomcat server'){
            steps{
                sh "curl -v -T ${env.WAR_FILE} ${env.TOMCAT_URL}/deploy?path=/app&update=true"
                }
        }
    }
}
