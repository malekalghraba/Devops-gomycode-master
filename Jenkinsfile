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
        
           sh 'mvn package' }}
    stage('SonarQube Analysis') { steps{ script{
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=mycode -Dsonar.projectName='mycode'"
    }
  }}}      

stage("Deployment stage") {
            steps {
                script {
                pom = readMavenPom file: 'pom.xml'
                   echo "${pom.artifactId}-${pom.version}.${pom.packaging}"
                   sh "mvn deploy:deploy-file  -DskipTests=true -DgroupId=${pom.groupId} -DartifactId=${pom.artifactId} -Dversion=${pom.version}  -DgeneratePom=true -Dpackaging=${pom.packaging}  -DrepositoryId=deploymentRepo -Durl=http://localhost:8081/repository/maven-releases/ -Dfile=target/${pom.artifactId}-${pom.version}.${pom.packaging}"
                }
            }
        }


}}

