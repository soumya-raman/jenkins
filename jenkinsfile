pipeline
{
    agent any
    stages
    {
        stage('ContinoiusDownload')
        {
            steps
            {
                git 'https://github.com/prasadcloud/maven2.git'
            }
        }
        stage('ContinoiusBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinoiusDeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '30b5067a-2639-40c4-9ff8-a6a867e86f5a', path: '', url: 'http://172.31.82.255:8080')], contextPath: 'test2', war: '**/*.war'
            }
        }
        stage('ContinoiusTesting')
        {
            steps
            {
               git 'https://github.com/prasadcloud/FunctionalTesting.git'
            }
        }
        stage('ContinoiusDelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '30b5067a-2639-40c4-9ff8-a6a867e86f5a', path: '', url: 'http://172.31.82.132:8080')], contextPath: 'prod3', war: '**/*.war'
            }
        }
    
    }
}
