
pipeline
{
    agent any
    stages
    {
        stage('continuousDownload')
        {
            steps
            {
                git 'https://github.com/AkashB1993/Maven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
         stage('continuousDepolyment')
        {
            steps
            {
          
				deploy adapters: [tomcat9(credentialsId: '14913ee1-760e-42cd-bd05-0d981085ad17', path: '', url: 'http://172.31.8.235:8080')], contextPath: 'testmaven1', war: '**/*.war' 
            }
        }
        stage('continuousTesting')
        {
            steps
            {
               git 'https://github.com/AkashB1993/functionaltesting.git'
       
               sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepileline@2/testing.jar'
              
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
               
				deploy adapters: [tomcat9(credentialsId: '14913ee1-760e-42cd-bd05-0d981085ad17', path: '', url: 'http://172.31.3.24:8080')], contextPath: 'testmaven2', war: '**/*.war'
            }
        }
    }
    
}
