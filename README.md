# Wild Rydes AWS Amplify Setup

## Module 1

This module guides you through configuring AWS Amplify to host the static resources for your web application with continuous deployment. The Amplify Console provides a git-based workflow, making deployment and hosting seamless. In subsequent modules, dynamic functionality will be added using JavaScript to call remote RESTful APIs built with AWS Lambda and Amazon API Gateway.

### Architecture Overview

The architecture is straightforward. AWS Amplify Console manages all static web content, and end-users access the site using the public URL provided by Amplify. No web servers are required.

### AWS Regions

This web application can be deployed in any AWS Region supporting services like AWS Amplify, AWS CodeCommit, Amazon Cognito, AWS Lambda, Amazon API Gateway, and Amazon DynamoDB. Refer to the [AWS Regional Services List](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) to find supported Regions.

## Setting Up Code Repository

### Step 1: Create CodeCommit Repository

- Open the AWS CodeCommit console.
- Choose Create Repository.
- Enter `wildrydes-site` for the Repository name.
- Choose Create.

### Step 2: Set Up IAM User and Git Credentials

- Set up an IAM user with Git credentials following instructions in the [AWS CodeCommit User Guide](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).

### Step 3: Configure AWS CLI

- If AWS CLI is not installed, install it using terminal commands specific to your OS.
- Enter `aws configure` in the terminal, providing Access Key ID, Secret Access Key, and Region.

### Step 4: Set Up Git Config

- For Linux, macOS, or UNIX machines, see Step 3 instructions for [Linux, macOS, or UNIX](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-unixes.html).
- For Windows machines, see Step 3 instructions for [Windows](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-windows.html).

### Step 5: Clone CodeCommit Repository

- Navigate to the AWS CodeCommit console.
- Select the `wildrydes-site` repository.
- Select Clone HTTPS from the Clone URL dropdown to copy the HTTPS URL.
- Run `git clone` in the terminal using the copied URL.

### Step 6: Copy Website Content

- Change directory into your repository (`wildrydes-site`).
- Copy static files from S3 bucket:
    ```bash
    aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
    ```
- Add, commit, and push git files.

### Step 7: Launch AWS Amplify Console

- Launch the AWS Amplify console. 
- Choose Get Started. 
- Under the Amplify Hosting Host your web app header, choose Get Started. 
- On the Get started with Amplify Hosting page, select AWS CodeCommit and choose Continue.
- On the Add repository branch step, select wildrydes-site from the Select a repository dropdown.
- If you used GitHub, you'll need to authorize AWS Amplify to your GitHub account.
- In the Branch dropdown select master and choose Next. 

## Module 2
In this module, you will integrate Amazon Cognito User Pools to manage user accounts on your WildRydes website. Users will register, confirm their email, and sign in to access the site. This README provides step-by-step instructions for the setup and usage of the authentication system.

## Prerequisites
- AWS account with appropriate permissions.
- Git installed on your local machine.

## Setup Instructions

1. **Clone the repository to your local machine:**

    ```bash
    $ git clone <repository-url>
    $ cd wildryde-site
    ```

2. **Module 1: Initial Setup**
   - Follow the steps outlined in the "Module 1 - Initial Setup" section.

3. **Module 2: User Registration and Sign-In**
   - Perform the steps mentioned in the "Module 2 - User Registration and Sign-In" section.

4. **API Configuration:**
   - Save the authentication token generated after successful sign-in.

5. **Notes:**
   - Ensure email verification for real email addresses.
   - Verify SES settings for email delivery.
   - Update Cognito details in `config.js`.

6. **Deployment:**
   - Commit and push the changes to your Git repository.

    ```bash
    $ git add .
    $ git commit -m "module_2_changes"
    $ git push
    ```

7. **Testing:**
   - Open your deployed website and test user registration, confirmation, and sign-in.

## Troubleshooting
- Check the Cognito console for user details and confirmations.
- Verify email delivery settings in the SES console.

## Next Steps
Proceed to Module 3 for integrating the Amazon Cognito user pool authorizer with the RESTful API using Amazon API Gateway.

## Important Notes
- This README assumes that you have successfully completed Module 1.
- Follow each step carefully to avoid issues with user registration and confirmation.
- For real deployments, configure Amazon SES for sending emails from your own domain.


