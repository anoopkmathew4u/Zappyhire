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
               sh 'mv /var/lib/jenkins/workspace/sam_ang/dist/zappy_boiler_plate/* /var/www/html'
               }
            }
        }
    }  
}   
