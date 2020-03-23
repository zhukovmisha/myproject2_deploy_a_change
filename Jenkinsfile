pipeline {          
    agent any
    stages { 
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM',                 
                branches: [[name: "origin/master"]], 
                userRemoteConfigs: [[
                url: 'https://github.com/zhukovmisha/myproject2_deploy_a_change.git']]])
            }
        }
        stage('Ansible Deploy') {            
            steps {
                ansiblePlaybook(
                    playbook: 'play.yml',
                    inventory: 'hosts',
                    become: true,
                    extraVars: [
                        name: "${env.WORKSPACE}"
                        ])
            }           
        }           
    }           
}
