pipeline {
    agent any

    tools {
        nodejs 'NODE_HOME'
    }
    
stages {
    stage('Getting project from Github') {
            steps {
                git branch : 'Iheb' ,
                    url : 'https://github.com/ihebhamdi/DevOpsFront.git',
                    credentialsId:"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";
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
                sh 'sudo docker build  -t ihebhamdi/achat_front .'
            }
        }
        stage('Docker login')
        {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u ihebhamdi -p dckr_pat_OaNAxtGSk9tP8ZPv8g08oIpcc4w'
            }    
       
        }
      stage('Push') {

			steps {
				sh 'docker push ihebhamdi/achat_front'
			}
		}
    }
}