node {

    stage('Chekcout') {
        checkout scm
    }
    
    stage('Containerize') {
        @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i
        docker.withRegistry('https://registry.hub.docker.com', 'dockercreds') {

                def customImage = docker.build("paramveerprakash/docnest")

                // Push the container to the custom Registry
                customImage.push()
        }
    }
    
}
