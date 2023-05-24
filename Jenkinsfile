pipeline {
    agent any
	    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('CodeCheckout') {
            steps {
               git credentialsId: 'git_credentials', url: 'https://github.com/edigagangadhar99/mwebrepo.git'
               echo 'CodeCheckout executed.'
            }
			}
        stage('CodeBuild') {
            steps {
                sh 'mvn clean install'
                echo 'CodeBuild executed.'
            }
			}
        stage('CodeDeploy') {
            steps {
               
        sshagent(['deploy_user']) {
		 sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pjob2/webapp/target/webapp.war ec2-user@65.0.74.68:/opt/apache-tomcat-9.0.75/webapps'
			echo ""
								}			
            }
			}
        }
    }
	
	
