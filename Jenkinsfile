pipeline
{
    agent any
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
        stage('sonar-code-analysis')
        {
            steps
            {
                withSonarQubeEnv('sonarqube-9') 
                { 
                    sh "mvn sonar:sonar \
                        -Dsonar.projectKey=sonar-maven \
                        -Dsonar.host.url=http://54.66.155.216:9000 \
                        -Dsonar.login=sqp_bb17797a98e7b975d83cf0bc0fab5e089c98116b"
                }
            }
        }
    }
}