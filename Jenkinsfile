pipeline{
     agent any 
     environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "http://localhost:8081/nexus/repository/releases/"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "Releases"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "admin:azerty"
              }

  stages{

      stage("clone "){

        steps{
           echo "getting project from git" 
           git url:'https://github.com/malekalghraba/Devops-gomycode-master '

 }}
     stage("mvn version"){ steps{
           sh 'mvn --version'}
}
      stage("mvn clean"){ steps{
           sh 'mvn clean '}}
      stage("creation du livrable"){ 
        steps{
        
           sh 'mvn package' }}
    stage('SonarQube Analysis') { steps{ script{
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=mycode -Dsonar.projectName='mycode'"
    }
  }}}      

stage("Deploiement dans nexus ") {
     		 steps{
                          
  			sh "mvn deploy"
                }

}



}}

