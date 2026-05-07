pipeline {
    agent any
    stages {
        stage('Clone code') {
        steps {
            echo "code already cloned by Jenkins, so no need to clone again"
        }
    }
    stage('build') {
        steps {
            echo "Building application..."
        }
    }
    stage('Test') {
        steps {
            echo 'running tests...'
        }
    }
    stage('Build docker image') {
        steps {
            bat 'docker build -t myapp:v2 .'
        }
    }
    stage('stop old container') {
        steps {
            bat 'docker stop mycontainer || exit 0'
        }
    }
    stage('Remove old container') {
        steps {
            bat 'docker rm mycontainer || exit 0'
        }
    }
    stage('run new container') {
        steps {
            bat 'docker run -d -p 8086:80 --name mycontainer myapp:v2'
        }
    }
}
}