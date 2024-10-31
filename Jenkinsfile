pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/chaewon0720/testlab.git', branch: 'main'
      }
    }

    stage('deploy and service') {
      steps {
        sh '''
        ansible master -m shell -a "sudo kubectl create deploy purple --replicas=3 --port=80 --image=chaewon0720/keduitlab:blue"
        ansible master -m shell -a "sudo kubectl expose deploy purple --type=LoadBalancer --port=80 --target-port=80 --name=purple-svc"
        '''
      }
    }
  }
}
