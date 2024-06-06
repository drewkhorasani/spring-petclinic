pipeline {
    agent any
    tools {
		jfrog 'jfrog-cli'
	}
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
        }
        stage('Deliver') {
            steps {
                sh 'mvn spring-boot:build-image'
                jf 'rt u target/ jfrog-interview-libs-snapshot-local/'
            }
        }
    }
}

