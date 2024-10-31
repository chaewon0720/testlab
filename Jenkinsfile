# Dockerfile
FROM nginx

ADD index.html /usr/share/nginx/html/

# index.html
<h2>jenkins test</h2>

# Jenkinsfile
pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/chaewon0720/testlab.git', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t chaewon0720/keduitlab:purple .
        sudo docker push chaewon0720/keduitlab:purple
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        sudo kubectl apply -f 
        '''
      }
    }
  }
}
