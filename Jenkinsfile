pipeline
{
agent any
stages{
    stage('SCM Checkout'){
	steps{
	echo 'Done.'
       }
    }
    stage('MVN Package'){
        def mvnHome = tool name: 'MAVENLOCAL', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        sh "${mvnCMD} clean package"
    }
}
}