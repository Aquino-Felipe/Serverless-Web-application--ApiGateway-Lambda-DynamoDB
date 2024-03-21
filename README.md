# Serverless Application README

![alt text](<Serverless-Web-application-[ApiGateway+Lambda+DynamoDB].drawio (1).png>)

This repository contains a serverless application built on AWS utilizing IAM, API Gateway, AWS Lambda, and DynamoDB. The application allows users to interact with a RESTful API where requests are processed by AWS Lambda functions written in Python and store information in a DynamoDB table.

## Overview

The application architecture follows the following flow:

1. **API Gateway**: Acts as the front-end for the application. All incoming requests are directed to the API Gateway.
2. **AWS Lambda**: Responsible for processing incoming requests. 
3. **DynamoDB**: Serves as the backend database where information from requests is stored.

## IAM Role Setup

Before deploying the Lambda functions, an IAM role needs to be created to grant necessary permissions to interact with LambdaFunction and DynamoDB. Follow these steps to set up the IAM role:

1. **Navigate to AWS IAM Console**: Go to the AWS IAM console at [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/).
2. **Create a New Role**: Click on "Roles" in the left sidebar, then click "Create role".
3. **Choose Lambda**: Under "Choose the service that will use this role", select "Lambda", and click "Next: Permissions".
4. **Attach Policies**: Search for and attach the policy `AWSLambdaBasicExecutionRole` and `AmazonDynamoDBFullAccess`. You can refine the permissions as needed based on your specific use case.
5. **Review and Name**: Review the role details and give it a meaningful name, e.g., `admin-lambda-role`. Then, click "Create role".

## Lambda Function Deployment

After creating the IAM role, the Lambda functions can be deployed. These functions will be associated with the IAM role created earlier to allow writing data to DynamoDB.

1. **Create Lambda Function**: Go to the AWS Lambda console at [https://console.aws.amazon.com/lambda/](https://console.aws.amazon.com/lambda/) and click "Create function".
2. **Choose Author from Scratch**: Select "Author from scratch" as the function blueprint.
3. **Configure Basic Information**: Enter a name e.g.`WebDemoFunction`and select Python 3.8 as the runtime.
4. **Choose or Create an Execution Role**: Select "Use an existing role" and choose the IAM role created earlier (`admin-lambda-role`).
5. **Create Function**: Click "Create function" to finish creating the Lambda function.
6. **Code Deployment**: Upload zip file in code folder `WebDemoFunction.zip`, this zip file contains html page and python code.

## DynamoDB Configuration

To set up the DynamoDB table for storing contact information:

1. **Navigate to DynamoDB Console**: Go to the DynamoDB console at [https://console.aws.amazon.com/dynamodb/](https://console.aws.amazon.com/dynamodb/).
2. **Create Table**: Click "Create table" and enter `contactustable` as the table name.
3. **Define Primary Key**: Set `email` as the partition key. You can add additional attributes as needed.
4. **Configure Settings**: (Optional) - Configure any additional settings such as provisioned capacity, autoscaling, etc.
5. **Create Table**: Click "Create table" to create the DynamoDB table.


## API Gateway Configuration

Now that the Lambda function is deployed, it needs to be integrated with API Gateway to handle incoming requests.

1. **Navigate to API Gateway Console**: Go to the API Gateway console at [https://console.aws.amazon.com/apigateway/](https://console.aws.amazon.com/apigateway/).
2. **Create a New API**: Click "Create API" and choose "REST API".
3. **Define API**: Choose "New API" and enter a name for your API e.g. `WebDemoAPI`. Click on create API.
4. **Create Resource and Method**: Create a resource and associated method (e.g., GET, POST, PUT, DELETE) for your API.
5. **Integration with Lambda**: Select the method (GET) and choose "Lambda Function" as the integration type. Enable lambda proxy integration, then, select the Lambda function you deployed earlier, click create method.
6. Select the method (POST) and choose "Lambda Function" as the integration type. Enable lambda proxy integration, then, select the Lambda function you deployed earlier, click create method.
7. **Deploy API**: Deploy your API to a new stage (e.g., production, development) to obtain an endpoint URL.

## Testing

After setting up the API Gateway, you can test the functionality of your serverless application by sending requests to the API endpoint obtained from the API Gateway console.

E.g `https://leqg48k106.execute-api.us-east-1.amazonaws.com/dev`

## Conclusion

This README provides an overview of the serverless application architecture utilizing IAM, API Gateway, AWS Lambda, and DynamoDB. Follow the provided steps to set up the necessary components and deploy the application successfully. For any further customization or troubleshooting, refer to the respective AWS documentation or seek assistance from AWS support.
