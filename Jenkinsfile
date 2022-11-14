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
        
        
        
        
           stage('docker')
        {
             steps {
                    script{
             sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                          }
                   }
          }         
        
        
         stage('push to dockerhub')
        {
             steps {
                    script{
             sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml --ask-become-pass"
                          }
                   }         
        }        
        
        
        
        
        
        
        }
        }
