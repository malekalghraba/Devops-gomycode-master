pipeline{
     agent any 
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

     /*  stage("lancement des tests unitaires"){ 
        steps{
           sh 'mvn test'}} */
       stage("Sonar") {
          steps {

            sh "mvn sonar:sonar"
                }
        }


}}
