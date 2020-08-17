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
		
		stage('preparing') { 
            steps {
                sh "cp ./target/employee-producer-0.0.1-SNAPSHOT.war /ansible-playbook/employee-producer-0.0.1-SNAPSHOT.war"
                
            }
        }
    }
}
