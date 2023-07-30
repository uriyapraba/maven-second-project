pipeline
{
    agent
    {
        label 'slave2'
    }
    tools
    {
        maven 'maven-3.6.3'
    }
    stages
    {
        stage('SCM_CHECKOUT')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/master']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/maven-second-project.git' ]
                ])
            }
        }
        stage('maven_build')
        {
            steps
            {
                sh 'mvn clean verify'
            }
        }
        stage('sonar-code-analysis')
        {
            withSonarQubeEnv('sonarqube-9.9.1') 
            { 
                sh 'mvn sonar:sonar'
            }
    }
}