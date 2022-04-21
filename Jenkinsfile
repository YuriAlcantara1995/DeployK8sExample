pipeline {
  agent any
  
    parameters {
  	choice choices: ['qa', 'prod'], description: 'Select namespace for deployment', name: 'DEPLOY_TO' 
   }

  
  environment {
  	MY_KUBECONFIG = credentials('k8sconfig')
  }
  
  stages {
    stage('Deploy K8s') {
      steps {
      	sh 'kubectl apply --kubeconfig ${MY_KUBECONFIG} -f application.yaml -n ${DEPLOY_TO}'
      }
    }
  }
}
