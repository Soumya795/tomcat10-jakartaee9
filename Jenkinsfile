pipeline {
    agent any
    tools {
        maven 'Maven' // The name you gave in the Maven tool configuration
    }

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Stage'
                withMaven(maven: 'Maven') {
                    // Log Maven version for debugging
                    sh 'mvn -version'
                    // Build the project with Maven
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the built .war file to Tomcat
                bat 'curl --upload-file ./target/*.war "http://localhost:8081/manager/text/deploy?path=/webapp&update=true" --user admin:admin'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Deployment succeeded!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
