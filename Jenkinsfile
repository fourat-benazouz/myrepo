pipeline {
    agent any 
    stages {
        
        stage('Clone') { 
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
        
        stage('Clean') { 
            steps {
                sh "mvn clean"
                
                
                
            }
        }
        
        stage('Compile') { 
            steps {
                sh "mvn compile"
                
            }
        }
        
        
        stage('packaging') { 
            steps {
                sh "mvn package"
                
            }
        }
    }
}
