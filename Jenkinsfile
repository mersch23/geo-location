pipeline{
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages{
        stage('maven build'){
            steps{
                sh 'mvn clean install package'
            }

        }
        stage('upload artifact'){
            steps{
               def mavenPom = readMavenPom file: 'pom.xml'
               nexusArtifactUploader artifacts:
               [[artifactId: "${mavenPom_artifactID}",
                classifier: '',
                 file: "target/${mavenPom_artifactId}-${mavenPom.version}.${mavenPom.packaging}",
                  type: "${mavenPom.packaging}"]],
                   credentialsId: 'nexusID',
                    groupId: "${mavenPom.groupId}",
                     nexusUrl: '198.58.98.193:8081',
                      nexusVersion: 'nexus2',
                       protocol: 'http',
                        repository: 'biom',
                         version: "${mavenPom.version}" 
            }

        }
        stage('list the dir'){
            steps{
                sh 'ls'
            }

        }
       
    }
}