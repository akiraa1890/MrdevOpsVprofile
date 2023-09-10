@Library('mysharedlibrary') _
pipeline {
    agent any 

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose Create/Destroy')
    }

    stages {
       
        stage('Git checkout'){
             when { expression { params.action == 'create' }}

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
             when { expression { params.action == 'create' }}

            steps {

                script {

                    mvnunitTest()

                }
            }

        }

        stage('mvn integration test'){
             when { expression { params.action == 'create' }}

            steps {

                script {

                    mvnintegrationTest()

                }
            }

        }


        stage('mvn checkstyle'){
             when { expression { params.action == 'create' }}

            steps {

                script {

                    mvncheckStyle()

                }
            }

        }


        stage('static code analysis'){
             when { expression { params.action == 'create' }}

            steps {

                script {
                    def SonarQubecredentialsId = 'MysonarToken'
                    staticcodeAnalysis(SonarQubecredentialsId)

                }
            }

        }

                stage('quality gate analysis'){
             when { expression { params.action == 'create' }}

            steps {

                script {
                    def SonarQubecredentialsId = 'MysonarToken'
                    qualityGate(SonarQubecredentialsId)

                }
            }

        }




    }
}
