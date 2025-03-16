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
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'
        }
      }
    }

    stage('Deploy to Remote Tomcat Server') {
      steps {
        sshagent(['jenkins-apache']) {
          sh 'scp -o StrictHostKeyChecking=no webapp/target/*.war ec2-user@172.31.13.128:/usr/share/tomcat/webapps/'
        }
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
