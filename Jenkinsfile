pipeline {    
    agent any 
    tools {
        maven 'maven3'
    }

    stages {
        stage (cleanws){
            steps {
        sh"cleanWs"
            }
        }
        stage(git checkout){
            steps {
                
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }

    }
}
