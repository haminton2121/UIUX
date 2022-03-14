pipeline {
    agent any
    stages {

        stage("replace")
        {
            steps
            {
                echo "Dockerfile"
                sh "./entrypoint.sh"
                echo "success"
            }
        }

        stage("Deploy")
        {
            steps
            {
                sh """ 
                docker build -t nginx:uiux --force-rm -f Dockerfile.template .
                docker run -it -p 8080:80 -d nginx:uiux
                """
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}