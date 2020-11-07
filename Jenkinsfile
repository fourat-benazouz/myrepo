pipeline {
    agent any 
    stages {
        
        stage('clone') { 
            steps {
                sh "rm -rf *"
                checkout([$class: 'GitSCM',
                branches: [[name: '*/master']],
                doGenerateSubmoduleConfigurations: false,
                extensions: [],
                submoduleCfg: [],
                userRemoteConfigs: [[url: 'https://github.com/fourat-benazouz/myrepo.git']]])
                sh "pwd"

                
            }
        }
        
        stage('clean') { 
            steps {
                sh "mvn clean"
                
                
                
            }
        }
        
        stage('compiler') { 
            steps {
                sh "mvn compile"
                
            }
        }
        
        
        stage('packaging') { 
            steps {
                sh "mvn package"
                
            }
        }
	stage('ansible-install colonnage de la VM CENTOS7') { 
                    steps {
               	        sh "ansible-playbook deploy-centos7.yml"                        
            }
	}
	 stage('Attente du power ON'){ 
		 steps {
		 	sleep 10 
	}
	    }
		stage('ansible-install jdk') { 
                    steps {
               	        sh "ansible-playbook installer-jdk.yaml"                        
            }
        }
	    stage('ansible-install and conifg tomcat') { 
                    steps {
               	        sh "ansible-playbook setup-tomcat.yaml"                        
            }
        }
	    
	    stage('Copy the war file') { 
                    steps {
               	        sh "ansible-playbook deploy.yaml"                        
            }
        }
    }
}
