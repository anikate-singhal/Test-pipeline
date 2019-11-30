node{
    stage('SCM Checlout'){
        git credentialsId: 'git-creds', url: 'https://github.com/anikate-singhal/learn.git'
    }
    stage('MVN Package'){
        def mvnHome = tool name: 'MAVENLOCAL', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        sh "${mvnCMD} clean package"
    }
}