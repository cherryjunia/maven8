node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/cherryjunia/maven8.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
        deploy adapters: [tomcat9(credentialsId: '43d974b7-ee84-4df4-91d1-0c63d27c091b', path: '', url: 'http://172.31.94.159:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        deploy adapters: [tomcat9(credentialsId: '43d974b7-ee84-4df4-91d1-0c63d27c091b', path: '', url: 'http://172.31.93.33:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
