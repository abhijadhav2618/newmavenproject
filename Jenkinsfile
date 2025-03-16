pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git 'https://github.com/abhijadhav2618/newmavenproject.git'
      }
    }

    stage("Package the code") {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'
        }
      }
    }

    stage('Deploy to Remote Tomcat Server') {
      steps {
        sh 'scp target/*.war ec2-user@13.126.197.78:/opt/tomcat/webapps/'
      }
    }
  }
}

 // stage('Sonar Scanning') {
    //   steps {

    //     withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {

    //     withSonarQubeEnv(credentialsId: 'sonar-token', installationName: 'sonar') {
    //       sh 'mvn clean package'
    //     }
    //     }
        
    //   }
    // }
