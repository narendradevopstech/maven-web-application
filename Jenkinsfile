node
{
    
    def mavenHome = tool name: "maven3.8.2"
    stage('checkoutcode'){
        
        git branch: 'development', credentialsId: 'af70cb5e-f994-467e-8a06-4c476c51901b', url: 'https://github.com/narendradevopstech/maven-web-application.git'
    }
        stage('build'){
            sh   "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.2/bin/mvn clean package"
        }
        stage('executesonarqubereport'){
        sh  "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.2/bin/mvn clean sonar:sonar"
        }
        stage('uploadartifactintonexusrepo'){
            sh  "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.2/bin/mvn clean deploy"
        }
        stage('deploytheappintotomcat')
        {
            sshagent(['ed55f594-283a-4d3a-b61d-630e911d5865']) {
         sh "scp -o  StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.133.159:/opt/apache-tomcat-9.0.53/webapps"


}
        }
        
  

        

        

}
