pipeline {
    agent any
    
    stages{
    
    
     /*   stage('Pull'){
            steps {
                echo 'Pulling..';
                  git branch: 'main',
                  url : 'https://github.com/wupti123/cdproject.git';
            }
        }
        */
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/wupti123/cdproject.git']]])
                }
            }
        }
      
        
        
        
        
          stage('Build'){
             steps { 
                    script{
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml --ask-become-pass"
                    }
                }
             }
        
        
        
        
        }
        }
