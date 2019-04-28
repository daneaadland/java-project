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
    
    stage('Deploy'){
        sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://hw10-jenkins-bucket/"
    }
   
    stage('Report'){
       withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    // some block
         
        sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1'
        }
    }    
}



