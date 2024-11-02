pipeline {    
    agent any 
    tools {
        maven 'maven3'
    }

    stages {
        stage (cleanws){
            steps {
        cleanWs()
            }
        }
        stage(git checkout){
            steps {
                git branch: 'main', url: 'https://github.com/kannanomy/boardgame.git'    
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage("sonarqube") {
            steps {
                def scannerHome=tool 'sonarscanner6'
                withSonarQubeEnv('sonar-pro') {
                    sh"${scannerHome}/bin/sonar-scanner
                    -Dsonar.projectKey=Boardgame"
                }
            }
        }
        stage("docker") {
            steps{
                sh'docker build -t docker65629 boardgame.' 
            }
        } 
        stage ('push image to dockerhub') {
            steps{
                withDockerRegistry(credentialsId: 'dock') {
                    sh 'docker push docker65629 boardgame'

                }
            }
        }  
    }
}