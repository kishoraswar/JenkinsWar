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
                    ls -lrt
                    //ssh -i "~/ubuntu.pem" ubuntu@ec2-13-127-255-103.ap-south-1.compute.amazonaws.com
                    scp -i ~/ubuntu.pem **/target/*.war ubuntu@ec2-13-127-255-103.ap-south-1.compute.amazonaws.com:/var/"
                       
                       ''' 
                }
            }
        }
    }
}
