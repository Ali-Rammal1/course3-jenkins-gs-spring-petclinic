pipeline {
    agent any

    stages {
        

        stage('Build') {
            steps {
                sh './mvnw package'
            }
        }

        stage('Tests') {
            parallel {
                stage('testsA') {
                    steps {
                        sh 'echo test A'
                        sleep time: 2, unit: 'SECONDS'
                        sleep time: 3, unit: 'SECONDS'
                        sh 'echo test A done'
                    }
                }
                stage('testsB') {
                    steps {
                        sh 'echo test B'
                        sleep time: 4, unit: 'SECONDS'
                        sh 'echo test B done'
                    }
                }
            }
        }

        stage('Capture') {
            steps {
                archiveArtifacts '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
}
