pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/japuter/Teht-v-Week5_Home-Assignment-_Jenkins-individual-assignment-.git', branch: 'master'


            }
        }

        pipeline {
            agent any

            stages {
                stage('Build') {
                    steps {
                        bat 'mvn clean install'
                    }
                }

                stage('Test') {
                    steps {
                        bat 'mvn test'
                    }
                }

                stage('Code Coverage') {
                    steps {
                        bat 'mvn jacoco:report'
                    }
                }
            }

            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                    jacoco execPattern: '**/target/jacoco.exec'
                }
            }
        }
