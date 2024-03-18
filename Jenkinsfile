pipeline {
    agent any
    options{
         buildDiscarder(logRotator(numToKeepStr: '5'))
        //disableConcurrentBuild()
    }
    triggers{
        cron('H * * * *') 
        pollSCM('H * * * *')
    }
    parameters{
        string(name:'DEPLOY ENV',defaultValue: 'Dev',description:"")
        choice(name:'CHOICE',choices:['dev','test','prod'],description:"Select Env")
    }
    environment{
        hostname="ip-172-31-39-95.ap-south-1.compute.internal"
        name="Kishor"
    }

    stages {
        stage('Checkout') {
            environment{
                myhome="Pune"
            }
            steps {
                echo 'code checkout'
                echo "$WORKSPACE"
                echo "$BUILD_ID"
                echo "$BUILD_NUMBER"
                echo "$BUILD_URL"
                
                echo "$hostname"
                echo "$name"
                echo "$myhome"
                
                script{
                    testvar="Mumbai"
                }
                echo "$testvar"
            }
        }
         stage('Build') {
            steps {
                    git 'https://github.com/kishoraswar22/spring-boot-war-example.git'
            }
        }
        stage('Test') {
            steps {
                echo 'code checkout'
            }
        }
         stage('Deploy') {
            steps {
                echo 'code checkout'
            }
        }
        
    }
     post {
         
         always{
             echo "this will execute every time"
         }
        success {
            emailext subject: "Build Successful: Job ${env.JOB_NAME} (${env.BUILD_NUMBER})", 
                      body: "The build of ${env.JOB_NAME} (${env.BUILD_NUMBER}) was successful.",
                      to: 'kishoraswar@gmail.com'
        }
        failure {
            emailext subject: "Build Failed: Job ${env.JOB_NAME} (${env.BUILD_NUMBER})", 
                      body: "The build of ${env.JOB_NAME} (${env.BUILD_NUMBER}) failed.",
                      to: 'kishoraswar@gmail.com'
        }
}
}
