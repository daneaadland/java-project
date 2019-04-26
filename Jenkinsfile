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
    
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIA5KHHKKMZHWDKVX5P', credentialsId: 'aws-credentials', secretKeyVariable: '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']]) {
        // some block
        sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1'
        }
    }

    
}



