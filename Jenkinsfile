pipeline
{
    agent
    {
        label 'slave1'
    }
    tools
    {
        maven 'maven-3.9.4'
    }
    stages
    {
        stage('SCM_CHECKOUT')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/branch1']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/maven-second-project.git' ]
                ])
            }
        }
        stage('maven_build')
        {
            steps
            {
                sh 'pwd ; ls -lrt'
                sh 'mvn clean package'
            }
        }
        /*stage('sonar-code-analysis')
        {
            steps
            {
                withSonarQubeEnv('sonarqube-9.9.1') 
                { 
                    sh 'mvn sonar:sonar'
                }
            }
        }*/
    }
}