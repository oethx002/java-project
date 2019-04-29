properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        git 'https://github.com/oethx002/java-project.git'
        sh "ant"
    }
    
    stage('Test'){
        sh "ant -buildfile test.xml"
    }
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
}
