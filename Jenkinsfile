pipeline{
    agent any
    environment {
        NETLIFY_STIE_ID = "544eca39-272b-410e-9515-9c1ab5e6462c"
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }

    stages {
        stage("build"){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    npm -v
                    node -v
                    npm i
                    npm run build
                '''
            }
        }

        stage('deploy'){
            steps{
                sh '''
                node_modules/.bin/netlify -v
                node_modules/.bin/netlify status
                node_modules/.bin/netlify deploy --dir=dist --prod
                node_modules/.bin/netlify status

                echo "done"
            '''
            }
        }
    }
}