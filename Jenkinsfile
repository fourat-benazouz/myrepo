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
		
		stage('ansible-install jdk') { 
                    steps {
               	        sh "cd /root/ansible-playbook/ && ansible-playbook installer-jdk.yaml"                        
            }
        }
    }
}
