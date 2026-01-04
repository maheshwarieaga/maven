pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                 git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
                 deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'ca134ab9-e8c3-4d89-b536-101e536443e6', path: '', url: 'http://172.31.15.135:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
            }
        }
        stage('Downloading')
        {
            steps
            {
                 deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'ca134ab9-e8c3-4d89-b536-101e536443e6', path: '', url: 'http://172.31.11.245:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
