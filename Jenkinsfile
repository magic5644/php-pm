pipeline {
    agent any
    stages {
        stage('Sonar') {
            steps {
                    withDockerContainer(args: '-v /project-root:/project-root', image: 'nikhuber/sonar-scanner:latest', toolName: 'myDocker') {
                    sh 'sonar-scanner'
                }
            }
           
        }
        stage('phpunit') {
            steps {
                    withDockerContainer(args: '-v /project-root:/project-root', image: 'php:latest', toolName: 'myDocker') {
                    sh 'composer install'
                    sh 'vendor/bin/phpunit'
                }
            }
           
        }
    }
}