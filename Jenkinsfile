pipeline  {
    agent any
    tools {
    maven 'apache-maven-3.6.3'}
        
    stages {

        stage('Build') {
            steps{
            sh "mvn clean package"
        }
        }
        

        stage('Publish') {
            steps{
            // login Azure
            
            sh 'cd /var/lib/jenkins/workspace/event-reporting_AzFunction/target/azure-functions/event-reporting-20230120091857774 && zip -r ../../../archive.zip ./* && cd ../../../'
            sh "az functionapp deployment source config-zip -g 'az_functions' -n 'azfunctionswin' --src archive.zip"
         
        }
        }
    }
}
