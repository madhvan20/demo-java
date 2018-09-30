pipeline { 
    agent any  
    stages { 
        stage('Build') { 
            steps { 
               echo 'This is a minimal pipeline.'
                sh 'mvn --version'
                sh 'mvn package'
            }
        }

        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    app = docker.build("veer/java-demo")
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }
                }
            }
        }


    }
}
