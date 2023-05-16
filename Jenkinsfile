pipeline {
    agent any
    stages {
        stage('Welcome') { 
            steps { 
               echo 'This is a DevSecOps pipeline created by AWSTechGuide' 
            }
        }
        stage('Pull Sources') {
            steps {
             git url: 'https://github.com/kiriti07/tomcat-webapp.git', branch: 'main'
            }
         }
        
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
	    
	      stage ('Deploy') {
          steps {
			sh "cd /var/lib/jenkins/workspace/Build-WebApp/target/"
			sh "aws s3 cp webapptest.war s3://artifactory-aws-war/"
                //sh "scp -o StrictHostKeyChecking=no Webapp-Pipeline/target/webapptest.war ec2-user@13.233.106.41:/home/ec2-user/apache-tomcat-9.0.75/webapps/webapptest.war"
                }
	    }  	       
    }
}
