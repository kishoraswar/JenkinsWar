pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                    sh '''
                    pwd
                    ssh -i "ubuntu.pem" ubuntu@ec2-13-127-255-103.ap-south-1.compute.amazonaws.com
                    scp -i /home/jenkins/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
                       
                       ''' 
                }
            }
        }
    }
}
