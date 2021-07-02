#!groovy
node {
    
       def MAVEN_HOME = tool name:"M2_HOME", type:'maven'
       def mvnCMD = "${MAVEN_HOME}/bin/mvn"
        stage('checkout') {
                git credentialsId: 'BITBUCKET_CREDENTIAL', url: 'https://SuneelVenkata@bitbucket.org/SuneelVenkata/sampleapp.git'
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
