### FrontEnd Deploy Script: 

    aws s3 cp --recursive ./www s3://abanob-udagram/

# S3 Frontend (abanob-udagram)

![S3 Frontend](./screenshots/S3/S3_Frontend.png)

### BackEnd Deploy Script:
 
    - eb init udagram-api --platform node.js --region us-east-2

    - npm run build

    in ./elasticbeanstalk/config.yml add :
    deploy:
    artifact: www/Archive.zip

    - eb create --sample udagram-api-dev
    - eb use udagram-api-dev
    - eb deploy

# Elastic Beanstalk

![Elastic Beanstalk](./screenshots/Elastic%20Beanstalk/EB_1.png)

## add environment variables: in bin/deploy.sh
    
    eb setenv PORT=$PORT &&
    eb setenv DB_PORT=$DB_PORT &&
    eb setenv POSTGRES_HOST=$POSTGRES_HOST &&
    eb setenv POSTGRES_DB=$POSTGRES_DB &&
    eb setenv POSTGRES_USERNAME=$POSTGRES_USERNAME &&
    eb setenv POSTGRES_PASSWORD=$POSTGRES_PASSWORD &&
    eb setenv AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID &&
    eb setenv AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY &&
    eb setenv AWS_REGION=$AWS_REGION &&
    eb setenv AWS_PROFILE=$AWS_PROFILE &&
    eb setenv AWS_BUCKET=$AWS_BUCKET &&
    eb setenv JWT_SECRET=$JWT_SECRET &&
    eb setenv URL=$URL

# Elastic Beanstalk ENV

![Elastic Beanstalk Health](./screenshots/Elastic%20Beanstalk/EB_Health.png)

# Elastic Beanstalk Health

![Elastic Beanstalk Health](./screenshots/Elastic%20Beanstalk/EB_Health.png)

    
### Pipeline Jobs: 

## 1- Install Dependencies for Front & BackEnd Commands:
    
   - cd udagram-api && npm install
   - cd udagram-frontend && npm install -f

# Pipeline diagram

![Pipeline diagram](./screenshots/Diagram/pipline_CircleCI.png)

# Pipline main steps

![pipline - main - steps](./screenshots/CircleCI/CircleCI_Main_steps.png)

    
## 2- Build BackEnd & FrontEnd Commands:
    
   - cd udagram-api && npm build
   - cd udagram-frontend && npm build

# CircleCI Build steps

![CircleCI - Build - steps](./screenshots/CircleCI/CircleCI_Build_steps.png)


## 3- Deploy FrontEnd & BackEnd Commands:
   
   - cd udagram-api && npm deploy
   - cd udagram-frontend && npm deploy

# CircleCI Deploy step

![CircleCI - Deploy - steps](./screenshots/CircleCI/CircleCI_Deploy_steps.png)


## CircleCI Environment Variables

![CircleCI - Environment - Variables](./screenshots/CircleCI/CircleCI_ENV.png)
