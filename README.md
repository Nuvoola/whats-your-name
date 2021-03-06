# What's Your Name?

## Setup

#### Clone the repo

```bash
git clone https://github.com/pimlock/whats-your-name.git
cd whats-your-name
```

#### Install dev dependencies (make sure you are using Python3)

```bash
pip install -r dev-requirements.txt
```

#### Create Virtualenv:

```bash
virtualenv venv
source venv/bin/activate
```

#### Create CloudFormation stack

This step requires your AWS credentials to be set up:
* as `export AWS_ACCESS_KEY_ID=""; export AWS_SECRET_ACCESS_KEY=""`
* stored in `~/.aws/credentials`
* as `your_aws_region`
* stored in `~/.aws/config`

For more information about credentials, you can see [Set up AWS Credentials and Region for Development](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-credentials.html)

Create required S3 buckets:

1. Where CloudFormation will upload Lambda code to (`CODE_DEPLOYMENT_BUCKET`)

```bash
# To create a Bucket Sign open the Amazon S3 console at  https://console.aws.amazon.com/s3/. You must use the Bucket name filed for my-bucket 
# this bucket is where the zip file with AWSLambda code will be uploaded (it's used by CloudFormation to deploy Lambda)
export CODE_DEPLOYMENT_BUCKET=my-bucket

# creates deployable package for CloudFormation
scripts/package.sh

export REKOGNITION_COLLECTION_ID=collection-id
export FACES_BUCKET_NAME=bucket-name

# creates/updates the CloudFormation stack
scripts/deploy.sh
```

&copy; 2018 Piotr Mlocek. This project is licensed under the terms of the MIT license.
