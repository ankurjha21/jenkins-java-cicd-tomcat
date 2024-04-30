pipeline{
    agent any
    
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
    }
}
