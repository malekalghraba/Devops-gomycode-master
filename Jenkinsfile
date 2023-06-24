pipeline{
     agentany 
  stages{

      stage("clone "){

        steps{ 
           git url:'https://github.com/malekalghraba/Devops-gomycode-master '

 }}
     stage("mvn build"){ steps{
           sh 'mvn clean install'}
}

}
