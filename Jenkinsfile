pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git 'https://github.com/abhijadhav2618/newmavenproject.git'
      }
    }

    stage("validate the code") {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn validate'
          echo "webhook added verify"
        }
      }
    }

    stage("Compile the code") {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn compile'
        }
      }
    }

    stage("Test the code") {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn test'
        }
      }
    }

    stage("Package the code") {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn package'
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
