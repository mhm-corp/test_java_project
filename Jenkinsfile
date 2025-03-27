pipeline {
     agent {
            kubernetes {
                yaml """
    apiVersion: v1
    kind: Pod
    spec:
      containers:
        - name: gradle
          image: gradle:8-jdk21  # Image with Gradle and Java 21
          command: ["/bin/sh", "-c"]
          args: ["cat"]  # Keep container running
          tty: true
    """
            }
        }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mhm-corp/test_java_project.git'
            }
        }
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
}
