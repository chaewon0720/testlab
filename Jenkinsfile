pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/chaewon0720/testlab/', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t brian24/cicdtest:purple .
        sudo docker push brian24/cicdtest:purple
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        ansible master -m command -a 'kubectl create deploy web-green --replicas=3 --image=brian24/cicdtest:green'
        ansible master -m command -a 'kubectl expose deploy web-green --type=LoadBalancer --port=80 --target-port=80 --name=web-green-svc'
        '''
      }
    }
  }
}
