node {
  def myGradleContainer = docker.image('gradle:jdk8-alpine')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-u 0 -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-u 0 -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle run'
     }
  }
}
