pipeline {
    agent any

    stages {
        stage("SCM Check IN") {
            steps {
                git 'https://github.com/punehim/Jenkins_Upgradev3.git'
            }
        }
        stage("Install") {
            steps {
                 sh 'mvn -f java-tomcat-sample/pom.xml clean install'
            }
        }
        stage("Artifacts Archiving") {
            steps {
                echo "Now Archiving the Artifacts...."
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage("DeployinginTomcat") {
            steps {
                sshagent(['deplot-in-Tomcat']) {
                sh "scp -o StrictHostKeyChecking=no java-tomcat-sample/target/java-tomcat-maven-example.war ec2-user@34.202.143.104:/opt/tomcat/apache-tomcat-9.0.62/webapps"
             }
            }
        }
    }
}


pipeline {
    agent any

    stages {
        stage("SCM Check IN") {
            steps {
                git 'https://github.com/punehim/Jenkins_Upgradev3.git'
            }
        }
        stage("Install") {
            steps {
                 sh 'mvn -f java-tomcat-sample/pom.xml clean install'
            }
        }
    }
}