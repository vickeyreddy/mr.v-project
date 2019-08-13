node{

   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/python-docker-app-openshifts.git'
      }
   stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/itrainavengers/sonar-maven.git'
    }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean install'
     }
    }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
             //sh 'mvn clean package sonar:sonar'
             sh 'mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar' +
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=itrainavengers '+
             ' -Dsonar.login=c1f3a8036d378aacc1f6e6e2fc6dcd7de2ebae5d '
         //}
      }
    }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn package'
     }

    }
   stage('Docker Build') {
     def app = docker.build "vickeyreddy/python-docker-app"
    }

   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'Github-ID', url: 'https://index.docker.io/v1/']) {
          sh 'docker tag vickeyreddy/python-docker vickeyreddy/python-docker'
          sh 'docker push vickeyreddy/python-docker:001'
          sh 'docker push vickeyreddy/python-docker:latest'
      }
    }

   stage("App deployment started"){
     sh 'oc login --token=nYolyX-cqohjHOU4vjJiwNo18YOgemhRldkzBRoXY-E --server=https://api.us-east-2.online-starter.openshift.com:6443'
     //sh 'oc new project python-docker'
     sh 'oc  import-image vickeyreddy/python-docker:pattabhi-1.0 --name python'
     sh 'oc expose svc python-app2 --name=python-app'
     sh 'oc status'
    }

    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }


























}
