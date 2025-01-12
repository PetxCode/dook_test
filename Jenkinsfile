pipeline{
    agent any

    environment {
        NETLIFY_SITE_ID = "544eca39-272b-410e-9515-9c1ab5e6462c"
        NETLIFY_TOKEN = credentials('netlify-token')
        
    }

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
                   
                    node_modules/.bin/netlify -v


                    node_modules/.bin/netlify --dir=dist --prod

                    node_modules/.bin/netlify -status
                    
                '''
            }
        }
    }
}
