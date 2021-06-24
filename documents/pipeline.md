### Pipeline process

#### Platform

This app uses Circle CI for the CI/CD.
Github is a main repository and collaborates with Circle CI for the purpose of the automated integration and deployment.

#### Orbs

This app uses three orbs.
・circleci/node@4.1.0
・circleci/aws-cli@2.0.3
・circleci/aws-elastic-beanstalk@1.0.0

#### Jobs

There are two main jobs.
・Build
・Deploy

#### Flow

The outline of the pipeline flow is found in screenshots folder of root.
But I write short description below for the detail.

・Build

1. First, build job starts
2. Then, frontent installation starts. Dependencies in udagram-frontend folder are installed in this process.
3. After the installation finishes, backend installation starts. Dependencies in udagram-api folder are installed.
4. Frontend build starts. All built files go into /www folder.
5. Backend build starts. All built files go into /www folder.

・Deploy
This is almost the same as Build process.
But two more processes for deployment. This happens only when changes are made on main branch.

6.  Deploy the frontend files built at step 4 to S3.
7.  Deploy the backend files built at step 5 to Elastic Beanstalk.
8.  Check health status of the server. The status should be OK.
