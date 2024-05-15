pipeline {
    agent any
    tools {
        maven 'Maven'
    }

    stages {

        stage('Build') {
            steps{
                 // withMaven(maven: 'Maven') {
                    // Build the project with Maven
                 bat 'C:\\ProgramData\\Jenkins\\.jenkins\\tools\\hudson.tasks.Maven_MavenInstallation\\Maven\\apache-maven-3.9.6\\bin\\mvn clean package'
                // }
              }
            }

        stage('Deploy') {
            steps {
                // Deploy the built .war file to Tomcat
                bat 'curl --upload-file ./target/*.war "http://localhost:8081/manager/text/deploy?path=/webapp&update=true" --user admin:admin'
            }
        }
    }
}
