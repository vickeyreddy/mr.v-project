node{
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/mr.v-project.git'
      }
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/vickeyreddy/mr.v-project.git'
    }
    stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withpython(python: 'pip') {
             //sh 'pip clean package sonar:sonar'
             sh ' sonar.python.file.suffixes:prepare-agent package sonar:sonar' +
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=itrainavengers '+
             ' -Dsonar.login=c1f3a8036d378aacc1f6e6e2fc6dcd7de2ebae5d '
         //}
      }
    }
}
