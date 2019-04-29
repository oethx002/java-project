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
        sh 'aws s3 cp target/java-project S3://jenkins/$(JOB_NAME)/$(BUILD_NUMBER)/'
    }
    
    stage('Report'){
        
    }
    

}
