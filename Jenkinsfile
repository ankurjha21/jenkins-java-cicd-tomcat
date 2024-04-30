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
        stage('Deploy on tomcat'){
            steps{
               sh set +x
               sh echo "Deploying to Tomcat at http://tomcat:8080/myapp"
               sh  curl -s --upload-file target/jb-hello-world-maven-0.2.0.jar "http://admin:12345@http://54.221.33.116:8090/manager/text/deploy?path=/myapp&update=true&tag=${BUILD_TAG}"
            }
        }
    }
}
