pipeline {
    agent any
    stages {
        stage ('Build Servlet Project') {
            steps {
                /*For windows machine */
               bat  'mvn clean package'
 
                /*For Mac & Linux machine */
               // sh  'mvn clean package'
            }
 
            post{
                success{
                    echo 'Now Archiving ....'
 
                    archiveArtifacts artifacts : '**/*.war'
                }
            }

            stage ('Deploy Staging Area Pipeline'){
                steps{

                    build job : 'Deploy-StagingArea-Pipeline'
                }
            }
        }
    }
}