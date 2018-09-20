pipeline {
    agent any
    tools {
        maven 'M3'
    }
    triggers {
        githubPush()
    }
    environment {
        WAR_NAME = '11hello-world' 
        DEPLOYMENT_PATH='/opt/wildfly/standalone/deployments'
        HOST_WILD = 'root@192.168.60.7'
        HOST_ART = 'http://192.168.60.8:8081/artifactory'
        MANAGER = 'admin@lawstrust.com'
        ARTIFACT = 'target/hello-world-war-1.0.0.war'
        REPOSITORIY = 'helloworld'
    }
    stages {
        stage('SCM') {
            steps {
                script {
                    cleanWs()
                        git url: 'https://github.com/GnitkoPavel/hook.git'
                }
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install"
            }
        }
    }
}
