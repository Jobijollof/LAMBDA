#  AWS-LAMBDA

# Creating an S3 bucket, from the console that is triggered by a Lambda function. Lambda is triggered everytime an object is added to the S3 bucket.

# Requirement:

- An AWS account.
- Basic understanding of a Lamdba function.
- Basic understanding of AWS S3 bucket.

# Architecture:

![Architecture](./images/architecture-lambda.png)

# Step 1.
- Log into you AWS account and search for S3
- Click on `Create bucket`
Under ***General Configuration*** do the following
- Enter bucket name (name must be globally unique without any space or upper letter case)
- Region, choose a region. Please note your region because your Lambda must be created in that same region

Under ***Object Ownership***
- Click on `ACLs disabled`

Under ***Block Public Access settings for this bucket***
- Uncheck block public access 

![unblock](./images/grant-access.png)

- Click acknowledgement

![Acknowlegement](./images/acknowledge.png)

Leave everyother option as default

Click on `Create bucket`

- Upload file into bucket click on `upload`

- Click on Permissions and drop bucket policy and `save`

- Click on Properties and enable static website hosting

- Once these are done, it means the bucket has now been made public 

# Step 2. Create a Lambda Function


