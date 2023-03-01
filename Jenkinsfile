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
               nexusArtifactUploader artifacts:
               [[artifactId: '${POM_ARTIFACTID}',
                classifier: '',
                 file: 'target/${POM_ARTIFACTID}-${POM_VERSION}.${POM_PACKAGING}',
                  type: '${POM_PACKAGING}']],
                   credentialsId: 'nexusID',
                    groupId: '${POM_GROUPID}',
                     nexusUrl: '198.58.98.193:8081',
                      nexusVersion: 'nexus2',
                       protocol: 'http',
                        repository: 'biom',
                         version: '${POM_VERSION}' 
            }

        }
        stage('list the dir'){
            steps{
                sh 'ls'
            }

        }
       
    }
}