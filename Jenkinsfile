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

	mvnHome = tool 'MAVENLOCAL' 
   //   sh "${mvnHome}/bin/mvn package"
if (isUnix()) {
               sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
            } else {
               bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
            }
   }
}
