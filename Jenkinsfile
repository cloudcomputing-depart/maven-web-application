node{
    
    def mavenhome=tool name:'maven3.9.2'
    echo "node name is:${env.NODE_NAME}"
    echo "job name is:${env.JOB_NAME}"
    echo "build number is :${env.BUILD_NUMBER}"
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    stage('checkoutcode'){
        git branch: 'development', credentialsId: '61c9ee28-b9b8-4a0b-9033-0c30bb77f2c1', url: 'https://github.com/cloudcomputing-depart/maven-web-application.git'
    }
    stage('build'){
        sh"${mavenhome}/bin/mvn clean package"
    }
  /*
    stage('executesonarqubereport'){
         sh"${mavenhome}/bin/mvn clean sonar:sonar"
    }
    stage('uploadartifactintonexus'){
          sh"${mavenhome}/bin/mvn clean deploy"
    stage('deployintotomcatserver'){
        sshagent(['882cedda-9f1f-4b4a-a9e8-640be4011313']) {
       sh"scp -o strictHostKeychecking=no target/maven-web-application.war ec2-user@172.31.5.245:/opt/apache-tomcat-9.0.76/webapps/"
       }
    }
*/
    }
    
}
