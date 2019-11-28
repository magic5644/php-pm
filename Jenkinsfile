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
        stage('composer') {
            steps {
                    withDockerContainer(args: '-v /project-root:/project-root', image: 'composer:latest', toolName: 'myDocker') {
                        sh 'php init --env=Development'
                        sh 'composer update --ignore-platform-reqs'
                        sh 'composer install --ignore-platform-reqs'
                }
            }
           
        }
        stage('phpunit') {
            steps {
                    withDockerContainer(args: '-v /project-root:/project-root', image: 'php:5.6', toolName: 'myDocker') {
                    sh './vendor/bin/phpunit --verbose -c phpunit.xml.dist'
                }
            }
           
        }

        stage("Publish Clover") {
            steps {
                step([$class: 'CloverPublisher', cloverReportDir: '/project-root', cloverReportFileName: 'clover.xml']) 
            }
        
        }
    
    }
}