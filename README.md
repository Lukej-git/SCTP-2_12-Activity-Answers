# SCTP-2_12-Activity-Answers

## 1. What is the purpose of the execution role on the Lambda function?
#### Purpose of the Execution Role on the Lambda Function
The execution role is an IAM role assigned to the Lambda function, granting it permissions to interact with AWS services. Its purpose is to allow the Lambda function to:

Read objects from the source S3 bucket (since the function is triggered by file creation).
Perform any additional operations needed, such as logging to Amazon CloudWatch or interacting with other AWS resources.

## 2. What is the purpose of the resource-based policy on the Lambda function?
#### Purpose of the Resource-Based Policy on the Lambda Function
The resource-based policy is an IAM policy attached to the Lambda function itself. It grants permission to external AWS services or other AWS accounts to invoke the Lambda function. In this case, the S3 bucket needs permission to invoke the function when a new file is created.

## 3. If the function is needed to upload a file into an S3 bucket, describe (i.e no need for the actual policies):
#### What is the needed update on the execution role?
If the Lambda function needs to upload files to an S3 bucket, the execution role must be updated to include:

s3:PutObject permission on the target S3 bucket, allowing the function to upload files.
s3:ListBucket permission (optional) if the function needs to check existing objects before uploading.

#### What is the new resource-based policy that needs to be added (if any)?
No additional resource-based policy is required unless another AWS account or service needs to invoke the Lambda function.
Since the Lambda function itself is uploading files to S3, it only needs execution role permissions, and S3 does not need to invoke the Lambda function in this new requirement.
