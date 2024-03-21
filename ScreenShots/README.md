# Serverless Application README

This repository contains a serverless application built on AWS utilizing IAM, API Gateway, AWS Lambda, and DynamoDB. The application allows users to interact with a RESTful API where requests are processed by AWS Lambda functions written in Python and store information in a DynamoDB table.

## IAM ROLE for Lambda and DynamoDB

![IAM Role for Lambda and DynamoDB](1-IAM-Role-Lambda+Dynamo.png)

An IAM role is created to grant necessary permissions for Lambda and DynamoDB.

## Creating Lambda Function

![Creating Lambda Function](2-WebDemoFunction.png)

The process of creating a Lambda function for the application.

## Creating DynamoDB Table

![Creating DynamoDB Table](3-Creating-DynamoDB-Table.png)

Steps to create a DynamoDB table named "contactustable" with the partition key as "email".

## Creating API Gateway

![Creating API Gateway](4-Creating-APIGateway.png)

Setting up API Gateway for the application.

### Method Types for API

#### GET Method

![Method Type API GET](5-Method-Type-API-GET.png)

#### POST Method

![Method Type API POST](6-Method-Type-API-POST.png)

Illustrating the creation of methods (GET and POST) for the API.

## Testing Application

![Testing Application](7-Testing-Application.png)

Guidelines for testing the application after setup.

### Successful Message

![Successful Message](8-Succefull-message.png)

Confirmation message for successful execution.

## Checking DynamoDB Table

![Checking DynamoDB Table](10-DynamoDB-Table-Test-Validation.png)

Instructions for validating and checking the DynamoDB table.
