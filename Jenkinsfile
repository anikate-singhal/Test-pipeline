node{
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
	stage('Artifactory configuration'){

steps {

script {
rtMaven.tool ='Maven-3.5.3'

rtMaven.deployer releaseRepo: 'libs-release-local', 'libs-snapshot-local', server: server

rtMaven.resolver releaseRepo:'libs-release', snapshotRepo: 'libs-snapshot', server: server

rtMaven deployer.artifactDeploymentPatterns.addExclude("pom.xml")

buildInfo = Artifactory.newBuildInfo()

buildInfo.retention maxBuilds: 10, maxDays: 7, deleteBuildArtifacts: true

buildInfo.env.capture = true
}
}
	}
}
