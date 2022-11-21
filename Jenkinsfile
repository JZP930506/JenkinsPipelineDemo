pipeline {
    agent any
    parameters{
     choice(name:'VERSION',choices:['2.0.0','2.0.2','2.3.0'],description:' choice is for deploy version')
     booleanParam (name:'execute',defaultValue:false,description:'')
    } 
    environment{
        NEW_VERSION='1.3.0'
    }
    options {
        disableConcurrentBuilds()
        retry(4)
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
                sh './gradlew check'
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
            junit 'build/reports/**/*.xml'
        }
    }
}
