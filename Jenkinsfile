pipeline{
    agent any
        stages{
            stage("SCM checkout"){
                steps{
                    git 'https://github.com/abhijadhav2618/newmavenproject.git'
                }
            }

            stage("Maven compile"){
                steps{
                    withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                        sh "mvn compile"
                    }
                }
            }

            stage("Maven test"){
                steps{
                    withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                        sh "mvn test"
                    }
                }
            }

            stage("Maven build"){
                steps{
                    withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                        sh "mvn clean package"
                    }
                }
            }

            stage("docker build"){
                steps{
                    sh "docker build -t abhijadhav2618/devops923:latest ."
                }
            }
        
    }
}
