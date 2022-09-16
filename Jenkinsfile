    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and Test') {
                steps {
                    // for build
                    sh "mvn -Dmaven.test.failure.ignore=true clean compile test"
                    // for unit testing
                    junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true, skipPublishingChecks: true)
                }
            }
        }
        post {
            always {
                echo 'I will always say Hello again!'
            
                emailext body: '', attachLog: true,
                to: "priti.ranga@testingxperts.com", 
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
    }
    }
    }
   
