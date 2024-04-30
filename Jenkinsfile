pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Deliver') { 
            steps {
                sh "chmod +x -R ${env.WORKSPACE}"
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
        stage("Build Image"){
            steps{
                sh "chmod +x -R ${env.WORKSPACE}"
                sh 'docker build -t my-node-app:1.0 .'
            }
            
        }
    }
}
