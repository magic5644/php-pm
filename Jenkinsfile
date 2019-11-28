pipeline {
    agent any
    stages {
        stage('Sonar') {
           withDockerContainer(args: '-v /project-root:/project-root', image: 'nikhuber/sonar-scanner:latest', toolName: 'myDockerSonarq') {
               sonar-scanner
           }
        }
    }
}