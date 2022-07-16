node
{
    def mavenhome = tool name : "maven3.8.6"
    
    echo "The job name is: ${env.JOB_NAME}"
   echo "The node name is:${env.NODE_NAME}"
   echo "The workspace path is:${env.WORKSPACE}"	
   echo "The nodelabel  is:${env.NODE_LABELS}"	
   echo "The build no is:${env.BUILD_NUMBER}"
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
    stage('checkout code') {git branch: 'development', credentialsId: '7ae5e49b-2ab0-420d-8046-6d70b88af3c6', url: 'https://github.com/devopsclass-may/maven-web-application.git'
}
    
    stage('build') {
        sh "${mavenhome}/bin/mvn clean package"
    }
     /*
    stage('execute sq report') {
     sh "${mavenhome}/bin/mvn clean sonar:sonar"
     
    }
    
    stage('upload artifacts nexus') {
        sh "${mavenhome}/bin/mvn deploy"
    }
    
    stage('deploy app into tomcat'){
    
    sshagent(['49e9a88d-1c0c-4f38-9e11-3357be71941c']) {
        sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.186.190:/opt/apache-tomcat-9.0.64/webapps/"
    }
    
}
*/
}
