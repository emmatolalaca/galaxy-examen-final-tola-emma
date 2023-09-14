pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker { image 'maven:3.6.3-openjdk-11-slim' }
            }
            steps {
                git credentialsId: 'github',
                    url: 'https://github.com/emmatolalaca/galaxy-examen-final-tola-emma.git',
                    branch: 'main'
                sh 'mvn -B verify'
            }
            post{
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
                }
            }
        }
    }
}
