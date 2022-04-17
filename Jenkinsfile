pipeline {

    agent any

    stages {

        stage("Clean Up"){
            steps {
                deleteDir()

            }
        }
        stage("Clone Repo"){
            steps {
                sh "git clone https://github.com/punehim/dockerrepotest.git"
            }

        }
        stage ("Build"){
            steps {
                dir("dockerrepotest") {
                    sh "mvn clean install"

                }
            }

        }
        stage ("Test") {
            steps {
                dir("dockerrepotest") {
                    sh "mvn test"
                }
            }
        }
    }
}