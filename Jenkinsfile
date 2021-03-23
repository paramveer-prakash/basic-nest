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
        echo "${StackAction}"
        
        if(params.StackAction=="update"){
            sh "aws cloudformation update-stack --stack-name newjs3bucket \
            --template-body file://s3cft_new.yaml \
            --region 'us-east-1' \
            --parameters  ParameterKey=BName,ParameterValue=JenkinsBucket "
        }else if(params.StackAction=="create"){
            sh "aws cloudformation create-stack --stack-name newjs3bucket \
            --template-body file://s3cft_new.yaml \
            --region 'us-east-1' \
            --parameters  ParameterKey=BName,ParameterValue=JenkinsBucket "
        }else{
            echo "No action on stack"
        }
        
        
    }
    
}
