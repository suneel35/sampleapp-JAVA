#!groovy
node {
    
       def MAVEN_HOME = tool name:"M2_HOME", type:'maven'
       def mvnCMD = "${MAVEN_HOME}/bin/mvn"
        stage('checkout') {
                git url: 'https://github.com/suneel35/sampleapp-JAVA.git'
        }
    
        stage('Build') {
                sh "${mvnCMD} clean package"
            }
        stage('docker image') {
         sh "docker build -t sampleapp .
        }
       stage('docker run') {
        sh "docker run -d -p 8080:8080 --name sampleapp sampleapp

}
        post { 
        always { 
            cleanWs()
        }
    }
}
