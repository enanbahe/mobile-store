pipeline {
  agent {
    label 'awscli'
  }

  environment {
    MAJOR_VERSION = 1
    AWS_REGION = 'us-east-1'
    REPO_NAME = 'projects/mobile-store'
    ECR_URL = '641665903019.dkr.ecr.us-east-1.amazonaws.com'    
    REPO_FULL_NAME = '$REPO_NAME:$MAJOR_VERSION.$BUILD_NUMBER'
    REPO_URL = '$ECR_URL/$REPO_FULL_NAME'
    BUILD_ENV_DOCKER_PATH = './environments/build/'
  }

  stages {
    stage('build-env') {
      when {
        branch 'build-env'
      }
      steps {
        sh 'export AWS_DEFAULT_REGION=$AWS_REGION && aws ecr describe-repositories --repository-names $REPO_NAME &&   && aws ecr create-repository --repository-name $REPO_NAME'
        sh '$(aws ecr get-login --no-include-email --region $AWS_REGION)'
        echo '$REPO_FULL_NAME'
      }      
    }
  }
}
