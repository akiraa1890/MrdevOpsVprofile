@Library('mysharedlibrary') _
pipeline {
    agent any 

    stages {

        stage('Git checkout'){

            steps {

                script {

                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/akiraa1890/MrdevOpsVprofile.git"
                    )

                }
            }

        }

        stage('mvn Unit test'){

            steps {

                script {

                    mvnunitTest()

                }
            }

        }

        stage('mvn integration test'){

            steps {

                script {

                    mvnintegrationTest()

                }
            }

        }

    }
}
