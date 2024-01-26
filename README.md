# Wild Rydes AWS Amplify Setup

## Overview

This module guides you through configuring AWS Amplify to host the static resources for your web application with continuous deployment. The Amplify Console provides a git-based workflow, making deployment and hosting seamless. In subsequent modules, dynamic functionality will be added using JavaScript to call remote RESTful APIs built with AWS Lambda and Amazon API Gateway.

### Architecture Overview

The architecture is straightforward. AWS Amplify Console manages all static web content, and end-users access the site using the public URL provided by Amplify. No web servers are required.

### AWS Regions

This web application can be deployed in any AWS Region supporting services like AWS Amplify, AWS CodeCommit, Amazon Cognito, AWS Lambda, Amazon API Gateway, and Amazon DynamoDB. Refer to the [AWS Regional Services List](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) to find supported Regions.

## Setting Up Code Repository

### Step 1: Create CodeCommit Repository

1. Open the AWS CodeCommit console.
2. Choose Create Repository.
3. Enter `wildrydes-site` for the Repository name.
4. Choose Create.

### Step 2: Set Up IAM User and Git Credentials

1. Set up an IAM user with Git credentials following instructions in the [AWS CodeCommit User Guide](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).

### Step 3: Configure AWS CLI

1. If AWS CLI is not installed, install it using terminal commands specific to your OS.
2. Enter `aws configure` in the terminal, providing Access Key ID, Secret Access Key, and Region.

### Step 4: Set Up Git Config

- For Linux, macOS, or UNIX machines, see Step 3 instructions for [Linux, macOS, or UNIX](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-unixes.html).
- For Windows machines, see Step 3 instructions for [Windows](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-windows.html).

### Step 5: Clone CodeCommit Repository

1. Navigate to the AWS CodeCommit console.
2. Select the `wildrydes-site` repository.
3. Select Clone HTTPS from the Clone URL dropdown to copy the HTTPS URL.
4. Run `git clone` in the terminal using the copied URL.

### Step 6: Copy Website Content

1. Change directory into your repository (`wildrydes-site`).
2. Copy static files from S3 bucket:
    ```bash
    aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
    ```
3. Add, commit, and push git files.

## Deploying with AWS Amplify

### Step 1: Launch AWS Amplify Console

1. Launch the [AWS Amplify console](https://console.aws.amazon.com/amplify/).
2. Under Amplify Hosting, choose Get Started.
