node('master-node') 
{
    stage('Continues Download') 
    {
        git 'https://github.com/balajimanipi/jave-web-app.git'
    }
    
    stage('Continues Build') 
    {
        sh 'mvn package'
    }
    stage('Continues Deploy') 
    {
        sh 'scp /var/lib/jenkins/workspace/Spipeline/target/maven-web-app.war root@192.168.75.130:/var/lib/tomcat9/webapps/testenv.war'
    }    
    
    stage('Continues testing') 
    {
        git 'https://github.com/balajimanipi/FunctionlTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/Spipeline/testing.jar'
    } 
    stage('Continues Delivery') 
    {
        input message: 'Waiting for Approval from the DM'
        sh 'scp /var/lib/jenkins/workspace/Spipeline/target/maven-web-app.war root@192.168.75.132:/var/lib/tomcat9/webapps/prodenv.war'
    }      
    
}
