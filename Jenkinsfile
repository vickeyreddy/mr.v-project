node{
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/mr.v-project.git'
      }
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/vickeyreddy/mr.v-project.git'
    }
}
