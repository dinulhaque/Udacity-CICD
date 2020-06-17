pipeline{
        agent any
        stages {
            stage('Lint HTML.'){
                steps {
                    sh "tidy -q -e *.html"
                }
            }
            stage('Upload to AWS.') {
                steps {                   
                        withAWS(region:'eu-west-2', credentials:"aws-static"){
                        s3Upload(file:'index.html', bucket:'dinuls-cicd-3', path:'index.html')
                    }                             
               
                    sh 'echo "Hello World"'
                    sh '''
                        echo "Multiline shell steps works too"
                        ls -lah
                    '''
                  }

                }

            }
        }
