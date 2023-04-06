pipeline {
    agent any
    tools {
        maven "maven"
        jdk "JDK"
    }
    stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }
        stage('Build') {
            steps {
                dir("/var/lib/jenkins/jobs/pipelinemaven") {
                sh 'mvn -f pom.xml clean package'
                }
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: 'test/results/*.xml'
      )
      }
   } 
}
