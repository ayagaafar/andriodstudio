node {
  def app
  stage('Clone repository') {
    checkout scm
  }
  stage('Deploy image') {
    sh "export DEPLOYMENT_NAME=andriodstudio"
    sh "export IMAGE_NAME=manar21/android-studio"
    sh "export IMAGE_NAME_file=deployment"
    sh "chmod +x deploy.sh"
    sh "./deploy.sh"
  }
  stage('docker-hub') {
    docker.withRegistry("https://registry.hub.docker.com", 'docker-hub-credential') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
