pipeline {
    agent any

    stages {

        stage('Build') {
            steps{
                    // Build the project with Maven
                    bat 'mvn clean package'
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
