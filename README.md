# 🍓 FruitBasket – Beginner-Friendly Serverless API on AWS

Welcome to the **FruitBasket** project! 🎉  
This guide will help you **deploy and use a simple web API** that lets you **add fruits to a database** using **Amazon Web Services (AWS)** — no previous AWS experience required.

---

## 📚 What Is This?

FruitBasket is a cloud-based backend app. It allows you to send fruit data (like name and color) to an online database using a simple API call.

Under the hood, it uses:

- **AWS Lambda** – runs your code in the cloud
- **API Gateway** – gives you a URL to call your code
- **DynamoDB** – stores your fruit data
- **CloudFormation** – sets up everything automatically for you

---
📁 Deploying the FruitBasket App
Follow these steps to deploy the app to AWS.

### ✅ 1. An AWS Account  
If you don’t have one yet, [sign up here](https://aws.amazon.com/).

### ✅ 2. Install the AWS Command Line Interface (CLI)

Download and install the AWS CLI tool:  
[Install instructions for Windows, Mac, and Linux](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

### ✅ 3. Set Up Your AWS Credentials
Run the following command:

bash: aws configure

You’ll be asked for:

AWS Access Key ID

AWS Secret Access Key

Default region name (e.g., us-east-1)

Output format (you can type json)

These keys are generated from your AWS account. You can create them under:

IAM > Users > [Your Username] > Security credentials




## 🛠️ What You Need Before You Start

## ✅ Step 1 – Download the Project
Clone the GitHub repository:

bash
git clone https://github.com/Ottowski/Fruitbasket.git
cd FruitBasket
If you're not using Git, you can also download the ZIP file from GitHub and extract it manually.

## ✅ Step 2 – Deploy the Application with AWS CLI
Make sure you are in the folder that contains template.yaml. Then run:

bash
aws cloudformation deploy \
  --template-file template.yaml \
  --stack-name FruitBasketStack \
  --capabilities CAPABILITY_NAMED_IAM
This command creates all the needed resources:

A Lambda function

An API Gateway endpoint

A DynamoDB table

All necessary IAM permissions

Wait until the command finishes. It may take a few minutes.

## ✅ Step 3 – Find Your API URL
After deployment:

Go to API Gateway Console

Click on your API called FruitBasketApi

Click Stages → then Prod

You will see your Invoke URL, something like:

bash
https://abc123xyz.execute-api.us-east-1.amazonaws.com/prod
Add /fruit to the end to get your full endpoint:

bash
https://abc123xyz.execute-api.us-east-1.amazonaws.com/prod/fruit
Save this URL — you’ll use it next!

## 🚀 How to Use the API
You can test the API using:

Postman

Or curl in your terminal or Command Prompt

## ✅ Example: Use Postman
Open Postman

Create a new POST request

Enter your full URL:

arduino
https://your-api-url.amazonaws.com/prod/fruit
Click on the Body tab

Choose raw and set the type to JSON

Paste in this JSON example:

json
{
  "id": "1",
  "name": "Apple",
  "color": "Red"
}
Click Send

You should get this response:

json
{
  "message": "Fruit added!"
}
✅ Success! You've added a fruit to your cloud database.

## ✅ Example: Use curl (in Terminal)
Replace <your-api-url> with your actual URL:

bash
curl -X POST <your-api-url>/fruit \
  -H "Content-Type: application/json" \
  -d '{"id": "2", "name": "Banana", "color": "Yellow"}'
You should get:

json
{
  "message": "Fruit added!"
}

## 🔍 What Happens Behind the Scenes
When you call the API:

API Gateway receives your request

It runs your Lambda function

The function writes the data to DynamoDB

You get a confirmation response

It’s a fully serverless and scalable system!

## 🧑‍💻 About the Author
Otto Arvidsson
Fullstack Developer & Cloud Enthusiast

## 📃 License
This project is free to use for learning and personal development.
Feel free to fork it, modify it, and share it.