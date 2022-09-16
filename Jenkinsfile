    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build') {
                steps {
                    sh "mvn -Dmaven.test.failure.ignore=true clean compile test"
        
                    junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true, skipPublishingChecks: true)
                }
            }
        }
        post {
            always {
                mail to: 'priti.ranga@testingxperts.com',
                subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
                body: "${env.BUILD_URL} has result ${currentBuild.result}"
            }
        }
    }
       
   
   
