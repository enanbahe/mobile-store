pipeline {
  agent {
    label 'awscli'
  }

  environment {
    MAJOR_VERSION = 1
    AWS_REGION = 'us-east-1'
    REPO_NAME = 'mobile-store'
    ECR_URL = '641665903019.dkr.ecr.us-east-1.amazonaws.com'    
    REPO_FULL_NAME = '$REPO_NAME:$MAJOR_VERSION.${BUILD_NUMBER}'
    REPO_URL = '$ECR_URL/$REPO_FULL_NAME'
    BUILD_ENV_DOCKER_PATH = './environments/build/'
  }

  stages {
    stage('build-env') {
      when {
        branch 'build-env'
      }
      steps {
        sh 'ls -aR .'
      }      
    }
  }
}
