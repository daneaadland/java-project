properties([pipelineTriggers([githubPush()])]) 
    node('linux'){
        stage('Build'){
            git credentialsId: 'Github-access-token-for-jenkins', url: 'https://github.com/daneaadland/private-repo-w11.git'
        }
    }



