pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'githubcreds', url: 'https://github.com/sampath1623/testcase.git'
                
            }
        }
    }
	


    post {
        success {
            script {
                def isPullRequest = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.ghprb.GhprbCause) != null
                if (isPullRequest) {
                    

                    sh "curl -X POST http://3.23.6.46:8080/github-webhook/"
                } else {
                    echo "This build was not triggered by a pull request."
                }
            }
        }
    }
}
