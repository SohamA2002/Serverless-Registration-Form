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

# 🔹 Step 2: 
