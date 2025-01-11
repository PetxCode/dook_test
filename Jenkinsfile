pipeline{
        agent any
    stages{
        stage("build_code"){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            } 

            steps{
                sh '''
                    echo "Creating Pipeline"
                    echo "Creating Pipeline again"

                    npm -v
                    node -v
                '''
            }
        }
    }
}
