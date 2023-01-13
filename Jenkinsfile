// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            spec:
                containers:
                - name: maven
                  image: maven:3-openjdk-18
                  command:
                  - cat
                  tty: true
            '''
        }
    }
    stages {
        stage('Build') {
            steps {
                container('maven') {
                    sh 'mvn package'
                }
            }
        }
    }
}
