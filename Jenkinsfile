pipeline {

    agent any

    stages {
        stage("connect to deploy server"){

            environment { 
                SSH_CRED = credentials('kube-instance')
            }

            steps {
                //=============== THIRD APPROACH
                script {
                    sh """
                    #!/bin/bash
                    ssh -i $SSH_CRED -t -o StrictHostKeyChecking=no ubuntu@15.223.49.63 << EOF
                    cd ~/microservices-demo
                    git pull 
                    cd .. && kubectl apply -f ./release/kubernetes-manifests.yaml
                    exit
                    << EOF
                    """
                }
                
            }
        }
    }
}
