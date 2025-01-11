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

                    npm i
                    npm run build
                    ls -la
                '''
            }
        }
        stage("deploy_code"){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            } 

            steps{
                sh '''
                    echo "Creating Pipeline to deploy"
                    

                    npm netlify-cli -g
                    node_modules/bin/netlify -v

                    
                '''
            }
        }
    }
}
