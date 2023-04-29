pipeline
{
    agent any
    stages
    {
        stage('continuousdownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousdeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '34a4cfba-1723-405d-bc5c-8754f9e170ea', path: '', url: 'http://172.31.80.91:8080')], contextPath: 'testapp2', war: '**/*.war'
            }
        }
        stage('continuousdelivery')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline2/testing.jar'
            }
        }
        stage('continuoustesting')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '34a4cfba-1723-405d-bc5c-8754f9e170ea', path: '', url: 'http://172.31.80.136:8080')], contextPath: 'prodapp22', war: '**/*.war' 
            }
        }
    }
}
