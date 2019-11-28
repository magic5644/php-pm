pipeline {
    agent any
    stages {
        stage('Sonar') {
            steps{
                withDockerContainer(args: '-v /project-root:/project-root', image: 'nikhuber/sonar-scanner:latest', toolName: 'myDockerSonarq') {
                sonar-scanner
           }
            }
           
        }
    }
}