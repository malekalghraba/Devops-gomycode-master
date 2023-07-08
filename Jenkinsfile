pipeline{
     agent any 
     environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "http://localhost:8081/repository/maven-central/"
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
        
           sh 'mvn package -DskipTests=true'}}
       

stage("Deploiement dans nexus ") {
     		 steps{
                          
  			sh "mvn deploy"
                }

}
 /* stage("Deploiement dans nexus ") {
     		 steps{
              // If you are using Windows then you should use "bat" step
              // Since unit testing is out of the scope we skip them
      	sh "mvn deploy:deploy-file -DgroupId=tn.esprit.spring -DartifactId=timesheet-ci -Dversion=5.1 -DgeneratePom=true -Dpackaging=jar -DrepositoryId=deploymentRepo -Durl=http://localhost:8081/repository/maven-releases/ -Dfile=target/timesheet-ci-5.1.jar"
                }
            } */
       /* stage("lancement des tests unitaires"){ 
        steps{
           sh 'mvn test'}} */
      
   stage('SonarQube Analysis') { steps{ script{
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=mycode -Dsonar.projectName='mycode'"
    }
  }}}

}}

