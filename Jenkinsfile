pipeline{
     agentany 
  stages{

      stage("clone "){

        steps{
           echo "getting project from git" 
           git url:'https://github.com/malekalghraba/Devops-gomycode-master '

 }}
     stage("mvn build"){ steps{
           sh 'mvn clean install'}
}

}}
