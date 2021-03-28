node {

    stage('Chekcout') {
        checkout scm
    }
    
    stage('Containerize') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockercreds') {

                def customImage = docker.build("paramveerprakash/docnest")

                // Push the container to the custom Registry
                customImage.push()
        }
    }
    
}
