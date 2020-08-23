pipeline{
	agent any
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
		//withSonarQubeEnv('SonarQube7.1'){
		//	bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar'
		//	bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
		}

	stage('Artifactory configuration'){
		def server = Artifactory.server('Artifactory Version 7.4.3')
def rtMaven = Artifactory.newMavenBuild()
rtMaven.tool ='Maven-3.6.3'

rtMaven.deployer releaseRepo: 'Jenkins-integration', 'Jenkins-integrations', server: server

rtMaven.resolver releaseRepo:'Jenkins-integration', snapshotRepo: 'Jenkins-integrations', server: server

rtMaven deployer.artifactDeploymentPatterns.addExclude("pom.xml")

buildInfo = Artifactory.newBuildInfo()

buildInfo.retention maxBuilds: 10, maxDays: 7, deleteBuildArtifacts: true

buildInfo.env.capture = true
}
}
