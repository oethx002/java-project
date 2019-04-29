properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        git 'https://github.com/oethx002/java-project.git'
        sh "ant"
        sh "ant -f build.xml -v"
    }
    
    stage('Deploy'){

        }

        
    }
    
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-jenkins-id', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        // some block
            sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
    }
    

}
