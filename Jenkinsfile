pipeline {
    agent any
    environment { 
        SCANNER_HOME = tool 'sonar-scanner'
    }
    stages {
        stage('checkout'){
            steps{
                script{
                    git branch: 'main', changelog: false, poll: false, url: 'https://github.com/mpr399/https://github.com/mpr399/EAHP-Project-PHP.git'
                }
            }
        }
        stage("Sonarqube Analysis "){ 
            steps{ 
                withSonarQubeEnv('sonar-server') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=EAHP -Dsonar.projectKey=EAHP''' 
                }    
            }
        }
        stage('Quality Gate'){
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar-token'
                }
            }
        }
        stage('build'){
            steps{
                script{
                    sh 'cd $HOME/workspace/eahp/app && docker build -t mvpar/eahpapp .'
                    sh 'cd $HOME/workspace/eahp/db && docker build -t mvpar/eahpdb .'
                }
            }
        }
        stage('push'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'REGISTRY_PWD', usernameVariable: 'REGISTRY_USER')]) {
                        sh 'docker login -u=$REGISTRY_USER -p=$REGISTRY_PWD'    
                        sh 'docker push mvpar/eahpapp'
                        sh 'docker push mvpar/eahpdb'
                    }    
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                     sh "cd $HOME/workspace/eahp && docker-compose down && docker-compose up -d"
                }
            }
        }
    }
}
