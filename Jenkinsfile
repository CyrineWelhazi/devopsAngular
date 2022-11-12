pipeline {
    agent any

    tools {
        nodejs 'NODE_HOME'
    }
    
stages {
    stage('Getting project from Github') {
            steps {
                git branch : 'main' ,
                    url : 'https://github.com/CyrineWelhazi/devopsAngular.git';
            }
        }
        stage('Install') {
            steps { 
                sh 'npm install'
            }
        }
        stage('Build') {
          steps { 
              sh 'npm run build'
              }
        }
        
        stage ('Build our image'){
            steps{
                sh 'docker build -t syrine2205/devopsangular .'
            }
        }
        stage('Docker login')
        {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u syrine2205  --password Elle123456789'
            }    
       
        }
      stage('Push') {

			steps {
				sh 'docker push syrine2205/devopsangular'
			}
		}
    }
}