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
      //withSonarQubeEnv('SonarQube')  {
             //sh 'mvn clean package sonar:sonar'
             sh 'mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar' +
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=vickeyreddy '+
             ' -Dsonar.login=687e313ca00cffbce20bcf4dac718f29e44a3246 '
         //}
    }
}
