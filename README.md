# Secure IVR Solution with Amazon Connect

This project offers an AWS CloudFormation template and Lambda function code to establish a secure IVR solution using Amazon Connect, specifically designed to address the updates and challenges in the AWS ecosystem, including runtime compatibility and resource accessibility.

## Project Overview

Developed to bridge a resource gap for implementing secure IVR systems with Amazon Connect, this project updates the Python runtime for AWS Lambda functions and provides direct access to necessary Lambda function code packages (`DecryptCustomerInputPython.zip` and `DecryptCustomerInputNodeJS.zip`), which were not directly available previously.

## Why This Project?

- **Updated Python Runtime:** Transition from Python 3.6 to 3.9 for AWS Lambda, ensuring current support and compatibility.
- **Resource Accessibility:** Provides `DecryptCustomerInputPython.zip` and `DecryptCustomerInputNodeJS.zip` files directly, solving the issue of unavailable downloads for these critical components.
- **Comprehensive Setup Guide:** Includes detailed instructions for creating an S3 bucket via CLI, uploading the required files, and accurately configuring the CloudFormation template for deployment.

## Prerequisites

Before proceeding with the deployment, ensure you have the following:

- AWS CLI installed and configured with your AWS credentials. [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
- An AWS account with permissions to create S3 buckets, upload files, and create CloudFormation stacks.

## Setting Up Your Environment

### Creating and Configuring an S3 Bucket

1. **Create a New S3 Bucket:** Use the AWS CLI to create an S3 bucket in your preferred region:
    ```bash
    aws s3 mb s3://your-bucket-name --region your-region
    ```
    Replace `your-bucket-name` with a unique bucket name and `your-region` with your desired AWS region.

2. **Upload Required Files:** Upload the `ConnectDecryptv2.yaml`, `DecryptCustomerInputPython.zip`, and `DecryptCustomerInputNodeJS.zip` files to the bucket:
    ```bash
    aws s3 cp ConnectDecryptv2.yaml s3://your-bucket-name/
    aws s3 cp DecryptCustomerInputPython.zip s3://your-bucket-name/
    aws s3 cp DecryptCustomerInputNodeJS.zip s3://your-bucket-name/
    ```
<img src="https://raw.githubusercontent.com/ghtali/secure-ivr-solution-amazon-connect/main/images/s3-objects-image.png" width="1080">

### Preparing the CloudFormation Template

After uploading the files, obtain the S3 Object URL for the `ConnectDecryptv2.yaml` file from the S3 console under the object's properties. This URL is required for creating the CloudFormation stack.

### Deploying the CloudFormation Stack

1. **Access AWS CloudFormation:** Log in to your AWS Management Console and navigate to the CloudFormation service.

2. **Create a New Stack:** Select **Create stack** > **With new resources (standard)**. Under **Prepare template**, choose **Template is ready**. For the template source, select **Amazon S3 URL** and paste the S3 Object URL of your `ConnectDecryptv2.yaml` file that you obtained from the S3 bucket.

3. **Configure Stack Details:** Follow the on-screen instructions to input necessary details such as stack name and parameters. Ensure all configurations match your specific deployment requirements.

<img src="https://raw.githubusercontent.com/ghtali/secure-ivr-solution-amazon-connect/main/images/cloudformation-s3-url.png" width="1080">

4. **Review and Create:** Review your configuration and, if everything is correct, proceed to create the stack. AWS CloudFormation will now provision and configure the resources as defined in the template.

### You should get the same reult as I you see in the picture:

<img src="https://github.com/ghtali/secure-ivr-solution-amazon-connect/blob/main/images/stack-image.png?raw=true" width="1080">

## Additional Instructions and Best Practices

For further insights and best practices on creating a secure IVR solution with Amazon Connect, refer to the AWS blog: [Creating a Secure IVR Solution with Amazon Connect](https://aws.amazon.com/blogs/contact-center/creating-a-secure-ivr-solution-with-amazon-connect/).

## License

This project is licensed under the MIT License - see the LICENSE file for details.
