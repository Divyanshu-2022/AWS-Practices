# bin/bash

# Create EC2 directory
mkdir -p "Amazon Elastic Compute Cloud (EC2)"

# Change directory to EC2
cd "Amazon Elastic Compute Cloud (EC2)"

# Create Code Samples directory
mkdir -p "Code Samples"
cat <<EOF > "Code Samples/README.md"
# Code Samples

Welcome to the Code Samples section for Amazon EC2!

In this section, you'll find a variety of code samples written in different programming languages and using AWS SDKs. Each code sample serves as a self-contained guide, demonstrating how to perform specific tasks within EC2.

These code samples are designed to be practical and easy to understand, suitable for both beginners and experienced users. Whether you're launching EC2 instances, configuring security groups, or managing snapshots, you'll find helpful examples here.

Feel free to use these code samples directly in your projects or customize them to suit your specific requirements. Let's dive in and explore the possibilities of EC2 through code!

Happy coding!
EOF

# Create Best Practices directory
mkdir -p "Best Practices"
cat <<EOF > "Best Practices/README.md"
# Best Practices

Welcome to the Best Practices section for Amazon EC2!

In this section, we'll share valuable guidelines and recommendations to help you optimize your usage of EC2. Drawing from the collective experience of AWS architects, engineers, and industry experts, these best practices cover a wide range of topics.

Learn how to improve performance, enhance security, and reduce costs with practical tips and proven strategies. Whether you're deploying applications, managing instances, or architecting solutions, these best practices will empower you to make the most of EC2.

Explore the recommendations, implement them in your workflows, and elevate your EC2 deployments to new heights of efficiency and reliability!

Happy optimizing!
EOF

# Create Documentation directory
mkdir -p "Documentation"
cat <<EOF > "Documentation/README.md"
# Documentation

Welcome to the Documentation section for Amazon EC2!

In this section, you'll find a comprehensive library of reference materials covering various aspects of EC2 usage. Each document serves as a detailed guide, offering step-by-step instructions, best practices, and practical insights.

Whether you're setting up web servers, hosting databases, or deploying applications, you'll find comprehensive tutorials and how-to guides to help you succeed. Our clear and concise documentation is designed to cater to users of all levels, from beginners to seasoned professionals.

Navigate through the documentation, learn new skills, and unlock the full potential of Amazon EC2 for your projects and workloads!

Happy learning!
EOF

echo "EC2 directory structure and README.md files created successfully!"

# AWS CLI Example - Creating and Deploying a Lambda Function:
#!/bin/bash

# Set variables
FUNCTION_NAME="my-lambda-function"
HANDLER="lambda_function.handler"
ROLE_ARN="arn:aws:iam::123456789012:role/lambda-role"  # Replace with your IAM role ARN
ZIP_FILE="lambda_function.zip"

# Create Lambda function deployment package
zip -r $ZIP_FILE lambda_function.py

# Create Lambda function
aws lambda create-function \
    --function-name $FUNCTION_NAME \
    --runtime python3.8 \
    --role $ROLE_ARN \
    --handler $HANDLER \
    --zip-file fileb://$ZIP_FILE

# Invoke Lambda function
aws lambda invoke \
    --function-name $FUNCTION_NAME \
    --payload '{"key1": "value1", "key2": "value2"}' \
    output.json

# Display output
cat output.json

## Python Example - Creating and Deploying a Lambda Function with Boto3:

import boto3
import zipfile
import os

# Set variables
FUNCTION_NAME = 'my-lambda-function'
HANDLER = 'lambda_function.handler'
ROLE_ARN = 'arn:aws:iam::123456789012:role/lambda-role'  # Replace with your IAM role ARN
ZIP_FILE = 'lambda_function.zip'

# Create Lambda deployment package
with zipfile.ZipFile(ZIP_FILE, 'w') as zip:
    zip.write('lambda_function.py')

# Create Lambda client
lambda_client = boto3.client('lambda')

# Create Lambda function
with open(ZIP_FILE, 'rb') as f:
    response = lambda_client.create_function(
        FunctionName=FUNCTION_NAME,
        Runtime='python3.8',
        Role=ROLE_ARN,
        Handler=HANDLER,
        Code={
            'ZipFile': f.read()
        }
    )

# Invoke Lambda function
response = lambda_client.invoke(
    FunctionName=FUNCTION_NAME,
    Payload=b'{"key1": "value1", "key2": "value2"}'
)

# Display output
print(response['Payload'].read().decode('utf-8'))
