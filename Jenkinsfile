pipeline {
  agent {
    label 'awscli'
  }

  environment {
    MAJOR_VERSION = 1
    AWS_REGION = 'us-east-1'
    REPO_NAME = 'projects/mobile-store'
    ECR_URL = '641665903019.dkr.ecr.us-east-1.amazonaws.com'    
    BUILD_ENV_DOCKER_PATH = './environments/build/'
  }

  stages {
    stage('build-env') {
      when {
        branch 'build-env'
      }
      steps {
        sh 'export AWS_DEFAULT_REGION=$AWS_REGION && aws ecr create-repository --repository-name $REPO_NAME'
        sh '$(aws ecr get-login --no-include-email --region $AWS_REGION)'
        sh 'docker build -t $REPO_NAME:$MAJOR_VERSION.$BUILD_NUMBER $BUILD_ENV_DOCKER_PATH'
        sh 'docker tag $REPO_NAME:$MAJOR_VERSION.$BUILD_NUMBER $ECR_URL/$REPO_NAME:$MAJOR_VERSION.$BUILD_NUMBER'
        sh 'docker push $ECR_URL/$REPO_NAME:$MAJOR_VERSION.$BUILD_NUMBER'
      }      
    }
  }
}
