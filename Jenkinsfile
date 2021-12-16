node {
      parameters {
        string(defaultValue: ''720766170633.dkr.ecr.us-east-2.amazonaws.com/jenkins-ecr'', description: 'ECR', name: 'ecr', trim: true)
        string(defaultValue: 'ecr:us-east-2:aws-credentials', description: 'Credentials', name: 'creds', trim: true)
      }
    
    def app

    stage('Clone repository') {

        checkout scm
    }

    stage('Build image') {
        /* Referencing the image name in AWS */

        app = docker.build(params.ecr)
    }
    
    stage('Test image') {
    /* Empty */

    }

    stage('Push image') {
        /* Referencing the AWS registry. Tagging with the Jenkins build number and the latest tag */
        
        docker.withRegistry(params.ecr, params.creds) {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}



