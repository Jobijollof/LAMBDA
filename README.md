#  AWS-LAMBDA

Creating an S3 bucket, from the console that is triggered by a Lambda function. Lambda is triggered everytime there is an input or output to the S3 bucket.

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

- Click on ***Permissions*** and drop bucket policy and `save`

- Click on ***Properties*** and `enable static website hosting`

- Once these are done, it means the bucket has now been made public 

# Step 2. Create a Lambda Function

- In the AWS search bar type in Lambda

![Lambda console](./images/lambda.png)

- Click on `Create a function`

- Click on `Author from Scratch

# Under Basic information

```
Function name = Your choice
Runtime       = Node.js 12.x
Permission    = Default
```
![basic info](./images/basic-info.png)

- Click on `Create function`

The following message should pop up on your screen. 

![sucessful](./images/function-created.png)
# Add Trigger

- Click  `Add trigger`

# Under Trigger Configuratios

- Select S3

- Bucket: pick your S3 bucket name

- Event Type : "All objects create events"
This means that the trigger will go off once there is an input or output from the S3 bucket

- Acknowledge  Recursive invocation 

- Click `Add`

![trigger](./images/trigger-success.png)

- Click on `Test`

#  Under ***Test event***

```
Event name : name of your choice
Template:     Hello-world
JSON statement format: 
 {
  "key1": "place your name here",
  
  
}
```
- Click on `Save`

![my lambda](./images/mylambda.png)

# Modify a Lambda Function

- Click on `Code` on the Fuction.

- Replace the  default body of the  code with the following string in bracket

```
body: JSON.stringify('Hello ' + event.key1 + ' from Lambda!'),

```
![lambda](./images/codeJSON.png)

- Click on `Deploy`

![sucessful deploy](./images/sucessful-deploy.png)

- Click on `Configuration`

- Click on `Permissons`

![config](./images/cofig-perm.png)

- Edit `Executive role`

```
Description: your choice
Time out: your choice (i am picking 10 mins)
Execution role : Use an existing role
```
- Click on `Save`

- Click on `Test`

![exe](./images/lamda-execute.png)

![final](./images/execution-result.png)

# Add files to the S3 bucket.

- Go to S3 and upload a file or folder

- Go back to LAMBDA to check if it was triggered.

- Click on your `Function` to view details

- Click on `Monitor`

![invocation](./images/innvocations.png)

At the top right corner of innvocatiosn click the three dots

- Click `View in metrics`

- Cloud watch will load the innvocations
![lamda-invoked](./images/Lambda-triggered.png)

✨✨✨✨✨✨✨✨
















