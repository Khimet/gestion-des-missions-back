pipeline {
        agent any

        tools {
            // Install the Maven version configured as "maven-default" and add it to the path.
            maven "maven-default"
        }

        stages {
            stage('Build package'){
                steps {
                    // Build the package
                    sh 'mvn clean package'
                }
            }
            
         }
    
        post {
                    // If Maven was able to run the tests, even if some of the test
                    // failed, record the test results and archive the jar file.
                    success {
                    	script {
                    		if (${env.BRANCH_NAME} == 'master')
                    			discordSend description: 'GIT_COMMIT', footer: 'Khalil a réussi son build', image: '', link: 'env.BUILD_URL', result: 'SUCCESS', thumbnail: '', title: 'env.JOB_NAME', webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
                        		//archiveArtifacts 'target/*.jar'
                        }
                    
                    failure {
                    	discordSend description: 'GIT_COMMIT', footer: 'Khalil a échoué son build', image: '', link: 'env.BUILD_URL', result: 'FAILURE', thumbnail: '', title: 'env.JOB_NAME', webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
                    }
                
                 
                }
}