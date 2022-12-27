pipeline {
    agent any

    tools {
        jdk "jdk"
        git "git"
        maven "maven"
    }
    

    stages {
        stage("SCM-Checkout") {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/rajkumar2212/myapp.git'
            }
        }
        stage("Maven Build"){
            steps{
                // Run Maven on a Unix agent.
                sh "mvn clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
             post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    archiveArtifacts 'target/*.war'
                }
            }
        }
    }
}
