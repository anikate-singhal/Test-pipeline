node{
   stage('SCM Checkout'){
     git 'https://github.com/anikate-singhal/Test-pipeline'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'MAVENLOCAL', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
}