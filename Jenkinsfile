node {
  withDockerContainer(args: '-p 3001:3000', image: 'node:lts-bullseye-slim') {
    stage('Build') { 
      checkout scm
      sh 'npm install' 
    }
    stage('Test') { 
      checkout scm
      sh './jenkins/scripts/test.sh'
    }
    stage('Deliver') {
      checkout scm
      sh './jenkins/scripts/deliver.sh'
      input message: 'Finished using the web site? (Click "Proceed" to continue)'
      sh './jenkins/scripts/kill.sh'
    }
  }
}