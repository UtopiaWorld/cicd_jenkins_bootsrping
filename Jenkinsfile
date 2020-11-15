pipeline {
    agent any
    
environment {
               TARGET_SERVER = 'ubuntu@ip-172-31-40-46'
               ARTIFACT = '/var/jenkins_home/workspace/project/target/*.jar'
               
           }
           
    tools {
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
                git branch: 'main',
                url: 'https://github.com/UtopiaWorld/project.git'
                sh " cd petclinic | mvn clean package"
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp $ARTIFACT $TARGET_SERVER:~/app.jar'
                sh 'ssh $TARGET_SERVER  sudo systemctl restart petclinic'
            }
            }
        
    }
}

