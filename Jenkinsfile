pipeline {
    agent {
        docker {
            image 'maven:3.9.0-eclipse-temurin-11' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                withDockerServer(uri: 'tcp://localhost:2375') {
                    sh 'export DOCKER_TLS_VERIFY=0 && mvn -B -DskipTests clean package'
                }
            }
        }
    }
}