pipeline {
    agent any
    environment{
        NEW_VERSION='1.3.0'
    }
    options {
        disableConcurrentBuilds()
        retry(2)
    }
    stages {
        stage('Build') {
             steps {
                 echo 'building the application'
                 echo "building version ${NEW_VERSION}"
            }
        }
        stage('Test')
        {
             steps {
                echo 'testing the application'
            }
        }
        stage('Deploy') {
            when {
                expression {
                    params.execute
                }
            }
            steps {
                echo 'Hello World'
            }
        }
    }
    post {
        always {
            echo 'say goodbay'
        }
    }
}
