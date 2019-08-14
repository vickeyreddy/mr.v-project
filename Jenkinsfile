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
             //sh 'pylint clean package sonar:sonar' 
             sh 'pylint org.jacoco:jacoco-python-plugin:prepare-agent package sonar:sonar' +
             ' -Dsonar.projectKey=vickeyreddy_mr.v-project '+
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=vickeyreddy '+ 
             ' -Dsonar.login=486b6710478ccacf2b379be13fe087bc97f20624 ' 
         //}
   }
}
