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
                emailext subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'", "attachLog: true, attachmentsPattern: '/target/surefire-reports', body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""", "to: 'priti.ranga@testingxperts.com'"       }
    }
    }
   
   
