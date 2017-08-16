pipeline {
  agent {
    label 'awscli'
  }

  environment {
    MAJOR_VERSION = 1
    AWS_REGION = 'us-east-1'
    REPO_NAME = 'mobile-store'
    REPO_URL = '641665903019.dkr.ecr.us-east-1.amazonaws.com'
    BUILD_ENV_DOCKER_PATH = './environments/build/'
  }

  stages {
    stage('build-env') {
      steps {
        export AWS_DEFAULT_REGION=$AWS_REGION
        aws ecr create-repository --repository-name $REPO_NAME:MAJOR_VERSION.${BUILD_NUMBER}
        $(aws ecr get-login --no-include-email --region $AWS_REGION) 
        docker build -t $REPO_NAME:MAJOR_VERSION.${BUILD_NUMBER} ${BUILD_ENV_DOCKER_PATH} 
        docker tag $REPO_NAME:MAJOR_VERSION.${BUILD_NUMBER} $REPO_URL/$REPO_NAME:MAJOR_VERSION.${BUILD_NUMBER}
        docker push $REPO_URL/$REPO_NAME:MAJOR_VERSION.${BUILD_NUMBER}
      }      
    }
  }
}
