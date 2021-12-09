node {
    def app

    stage('Clone repository') {

        checkout scm
    }

    stage('Build image') {
        /* Referencing the image name in AWS */

        app = docker.build("[name of your AWS ECR repository]")
    }
    
    stage('Test image') {
    /* Empty */

    }

    stage('Push image') {
        /* Referencing the AWS registry. Tagging with the Jenkins build number and the latest tag */
        
        docker.withRegistry('720766170633.dkr.ecr.us-east-2.amazonaws.com/jenkins-ecr', 'ecr:us-east-2:aws-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}

