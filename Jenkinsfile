pipeline {
    agent any
    stages {
        stage('git clone'){
            steps {
               git branch: 'main', url: 'https://github.com/anoopkmathew4u/Zappyhire.git'
            }
        }
      stage('build'){
            steps {
               nodejs(nodeJSInstallationName: 'Nodejs 19.8.1'){
               sh 'npm install -g npm@latest'
               sh 'npm install -g npm@8.12.1'
               sh 'ng build'
               }
            }
        }
        stage('aws log') {
            steps {
              withCredentials([[
             $class: 'AmazonWebServicesCredentialsBinding',
             credentialsId: 'AWS_CONFIG',
             accessKeyVariable: 'AWS_ACCESS_KEY_ID',
             secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                    sh 'aws s3 cp /home/ec2-user/Zappyhire/dist/zappy_boiler_plate/ "s3://bucket1234432/" --recursive'
                    
                }                  
            }
        }
    }  
}   
