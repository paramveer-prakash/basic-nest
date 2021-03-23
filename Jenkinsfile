node {

    stage('Chekcout') {
        checkout scm
    }
    
    /*stage('Containerize') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockercreds') {

                def customImage = docker.build("paramveerprakash/docnest")

                // Push the container to the custom Registry
                customImage.push()
        }
    }*/

    stage('Deploy') {
        echo "${NestAppImageName}"
        sh "aws cloudformation update-stack --stack-name newjs3bucket \
        --template-body file://s3cft_new.yaml \
        --region 'us-east-1' \
        --parameters  ParameterKey=BName,ParameterValue=JenkinsBucket "
    }
    
}
