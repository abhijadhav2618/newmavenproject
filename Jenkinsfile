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
                    sh "docker build -t abhijadhav2618/newmaven:latest ."
                }
            }

            stage("Push image to docker hub"){
                steps{
                    withDockerRegistry(credentialsId: 'Docker_Hub_Cred',  url:"https://index.docker.io/v1/") {
                        sh "docker push abhijadhav2618/newmaven:latest"

                    }   
                }
            }     
    }
}
