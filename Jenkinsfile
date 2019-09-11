pipeline{
    agent any 
    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', 
              branches: [[name: '*/master']], 
               doGenerateSubmoduleConfigurations: false, 
               extensions: [], 
               submoduleCfg: [], 
                userRemoteConfigs: [[url: 'https://github.com/murali90/maven-project.git']]])
            }
        }
        stage ('build stage'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('archiving'){
            steps{
                echo 'archiving articafts'
                archiveArtifacts artifacts: 'weabapp/target/*.war'
            }
        }
        stage('building docker image'){
            steps{
                "docker build . -t tomcat-hello-world:${env.Build_ID}"
                
            }
        }
           
    }
}
