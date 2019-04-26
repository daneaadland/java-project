properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        git 'https://github.com/daneaadland/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
}



