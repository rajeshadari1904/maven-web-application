pipeline{

agent any

tools{
maven 'maven3.8.2'

}

stages{

  stage('CheckOutCode'){
    steps{
    git credentialsId: 'git', url: 'https://github.com/rajeshadari1904/maven-web-application.git'
	}
  }
  
  stage('Build'){
  steps{
  sh  "mvn clean package"
  }
  }
/*
 withSonarQubeEnv(credentialsId: 'mean') {
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
  
  
  
  stage('DeployAppIntoTomcat'){
  steps{
  sshagent(['nani']) { 
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ubuntu@172.31.87.111:/opt/apache-tomcat-9.0.50/webapps/"    
  }
  }
  }
  */
}//Stages Closing

post{

 success{
 emailext to: 'rajeshadari1904@gmail.com,mithuntechnologies@yahoo.com',
          subject: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          body: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          replyTo: 'rajeshadari1904@gmail.com'
 }
 
 failure{
 emailext to: 'rajeshadari1904@gmail.com,mithuntechnologies@yahoo.com',
          subject: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          body: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          replyTo: 'devopstrainingblr@gmail.com'
 }
 
}


}//Pipeline closing
