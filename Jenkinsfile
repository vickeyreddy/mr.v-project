node{

   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/mr.v-project.git'
      }
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/vickeyreddy/mr.v-project.git'
    }
    pipeline {
        agent none
        stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'python clean package sonar:sonar'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        }
      }
      
   stage('SonarQube analysis') {
      requires SonarQube Scanner 2.8+
      def scannerHome = tool 'SonarQube Scanner 2.8';
      withSonarQubeEnv('My SonarQube Server') {
      sh "${scannerHome}/bin/sonar-scanner"
          ' -Dsonar.projectKey=vickeyreddy_mr.v project '+
          ' -Dsonar.host.url=https://sonarcloud.io '+
          ' -Dsonar.organization=vickeyreddy '+
          ' -Dsonar.login=a836eb50d6a0b99306e6db9038c5d37e44d1cc8d '
    }
  }
}
