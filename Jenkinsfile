pipeline{
	agent any
	stages{
  stage('SCM Checkout'){
     git 'https://github.com/anikate-singhal/Test-pipeline'
   }
	stage('Stage 1'){
     echo "hello"
   }
	stage('Stage 2'){
    echo "world"
   }
  
	stage('Compile-Package'){
      // Get maven home path
    //  def mvnHome =  tool name: 'MAVENLOCAL', type: 'maven'  

//	mvnHome = tool 'MAVENLOCAL' 
   //   sh "${mvnHome}/bin/mvn package"
//if (isUnix()) {
   //            sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
     //       } else {
       //        bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         //   }
	   bat "mvn install"
   }
	stage('SonarQube Analysis'){
		withSonarQubeEnv('SonarQube7.1'){
			bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar'
			bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
		}


}
}
