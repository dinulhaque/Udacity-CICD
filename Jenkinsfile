pipeline{
        agent any
        stages {
            stage('Lint HTML'){
                steps {
                    sh 'tidy -q -e *.html'
                }
            }
            stage('Upload to AWS') {
                steps {
                    retry(3){
                        withAWS(region:'eu-west-2', credentials:'Jenkins'){
                        s3Upload(file:'index.html', bucket:'dinuls-cicd-3', path:'')
                    }                             
                }
            }
        }
    }
}