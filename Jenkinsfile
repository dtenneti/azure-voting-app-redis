pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "${GIT_BRANCH}"
            }
        }
        stage('Docker Build') {
            steps {
                  sh(script: 'docker images -a')
                  sh(script:"""
                    cd azure-vote/
                    sudo docker images -a
                    sudo docker build -t jenkins-pipeline .
                    sudo docker images -a
                    cd ..
                    """
                     )
            }
            post{
                success {
                    echo "Docker successful"
                }
                failure {
                    echo "App failed to start :(" 
                }
            }
        }

    }
}
