pipeline{
	agent any
	stages{
	stage('Stage 1'){
		steps{
     echo "hello"
		}
   }
stage ('Compile Stage') {
steps {
withMaven() {
bat'mvn clean compile'
}
}
}
stage ('Testing Stage') {
steps {
withMaven() {
bat'mvn test'
}
}
}
stage ('Install Stage') {
steps {
withMaven() {
bat'mvn install'
}
}
}
}
}
