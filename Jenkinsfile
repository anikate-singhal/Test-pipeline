def server = Artifactory.server('Artifactory Version 7.4.3')
def rtMaven = Artifactory.newMavenBuild()
pipeline{
	agent any
	stages{
  		stage('SCM Checkout'){
	 		steps {
            			script{
     					git 'https://github.com/anikate-singhal/Test-pipeline'
		  			}
	       			}
       		}

		stage('Stage 1'){
			steps {
            			script{
     					echo "hello"
					}
   				}
		}

		stage('Stage 2'){
			steps {
            			script{
     					echo "world"
					}
   				}
		}
    
   
  
		stage('Compile-Package'){
			steps {
            			script{
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
   				}
		}
    
     
	        stage('SonarQube Analysis'){
			steps {
            			script{
     					withSonarQubeEnv('SonarQube7.1'){
					bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar'
					bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
					}
   				}
			}
		}

		stage('Artifactory configuration'){
			steps {
            			script{
     					rtMaven.tool ="Maven-3.6.3"

rtMaven.deployer releaseRepo: 'Jenkins-integration', snapshotRepo: 'Jenkins-integrations', server: server

rtMaven.resolver releaseRepo:'Jenkins-integration', snapshotRepo: 'Jenkins integrations', server: server

					rtMaven deployer.artifactDeploymentPatterns.addExclude("pom.xml")

					buildInfo = Artifactory.newBuildInfo()
		  			}
	       			}
       		}

}
}
