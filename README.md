# 🚀 Serverless Registration Form

## 📃 Overview

The project involves building a serverless web application that allows users to submit their info through a registration form which will be then stored in a DynamoDB table.
This Project is a great way to learn about the basic of serverless architecture & how to build serveless application using AWS services.

---

## ⚙️Service Used
  * DynamoDB Table
  * Create IAM Role for Lambda Function
  * Set up an API gateway endpoint & enable CORS for cross domain request

---

## 📦 Setup Guide (Step-by-Step)

# 🔹 Step 1: Create DynamoDB Table

* We will create a dynamodb table that will store the data submitted through our registration form. for eg. "name", "email", "phone number" all those things should be taken care or should be transferred to our dynamodb table.
* So we will be also defining the table schema and setting the primary key as the primary key should be unique for each item in the table so in our project we will be choosing a suitable primary key based on our data. In this project we will use email as a primary key since it is unique for each user.

* DynamoDB --> Create Table --> Table Name: registration-table --> Partition key: email --> Create.

# 🔹 Step 2: Create IAM Role for Lambda Function

* We need to create an IM role that will allow our function to access dynamodb table.
* IAM - Role --> Name: RegistrationFormRole --> Permissions:1. CloudWatch Full Access 2. DynamoDB Full Access --> Create
* We need to provide the dynamodb full access for the Lambda function to read write and do whatever it wants on the dynamodb table & Cloud watch full access because we need to look for the logs.

# 🔹 Step 3: Create Lambda Function

* We are going to create the Lambda function in this step, we will create a Lambda function that will handle form submissions and store the data in our dynamodb table we will use python as our Lambda functions programming language, since it is easy to use and support the AWS SDK for python.
* Lambda --> Create Function --> Author from Scratch --> Function Name: registration-form-function --> Runtime: Python (Latest Version) --> Permission -- use an existing role-(RegistrationFormRole) --> Create Function
* Copy Lambda Function and paste it in code and Deploy it
* Now going to DynamoDB table to create some dummy entries
* DynamoDB --> Select for Table(registration-table) --> Create Items --> Add entires as email, name, phone, password --> Create Items

# 🔹 Step 4: Create API Gateway and Enable CORS

* Amazon API gateway --> REST API - Build --> Name: Registration-api --> Create API
* Create Resource --> Resource name:Register and path "/"(by-default) --> Enable CORS --> Create Resource
* Create POST method: Create Method --> POST --> Type: Lambda Function --> check the region is correct or not --> Lambda Function: "registration-form-function" --> Save
* Enable CORS --> check-box the both "OPTIONS" & "post" --> Enable
* Delpoy --> Deployment stage: new --> Stage name: prod --> Deploy
* Invoke URL will be created save it and paste the URL in Script.js. Replace it in place of API_INVOKE_URL
```bash
// Set up request
    xhr.open('POST', 'API_INVOKE_URL/register', true);
    xhr.setRequestHeader('Content-Type', 'application/json');
```
* 
