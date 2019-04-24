
pipeline {
    agent none 
    stages {
        stage('Example Build') {
            agent {
                docker {
                    image 'node:6-alpine' 
                    args '-p 3000:3000' 
                }
            }
            stages {
                stage('Build') { 
                    steps {
                        sh 'npm install' 
                    }
                }
            }
        }
        stage('Example Test') {
            agent { // Equivalent to "docker build -f Dockerfile.build --build-arg version=1.0.2 ./build/
                dockerfile {
                    filename 'Dockerfile.build'
                    dir 'build'
                    label 'my-defined-label'
                    additionalBuildArgs  '--build-arg version=1.0.2'
                } 
            } 
            steps {
                echo 'Hello, JDK'
                sh 'java -version'
            }
        }
        stage('Example Run') {
            agent {
                docker {
                    image 'node:6-alpine' 
                    args '-p 3000:3000' 
                }
            }
            stages {
                stage('Build') { 
                    steps {
                        sh 'npm install' 
                    }
                }
            }
        }
    }
}