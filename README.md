# Serverless-Architecture-Tejas - steps followed
Assignment 1: Automated Instance Management Using AWS Lambda and Boto3
1. Setup: - Create two EC2 instances. - Tag one of them as `Auto-Stop` and the other as `Auto-Start`.

2. Lambda Function Creation:  - Set up an AWS Lambda function.  - Ensure that the Lambda function has the necessary IAM permissions to describe, stop, and start EC2 instances.

3. Coding: - Using Boto3 in the Lambda function:  - Detect all EC2 instances with the `Auto-Stop` tag and stop them.

   - Detect all EC2 instances with the `Auto-Start` tag and start them.

4. Testing: - Manually invoke the Lambda function   - Confirm that the instance tagged `Auto-Stop` stops and the one tagged `Auto-Start` starts.

     Assignment 2: Automated S3 Bucket Cleanup Using AWS Lambda and Boto3
   
1. S3 Setup:  - Navigate to the S3 dashboard and create a new bucket.

   - Upload multiple files to this bucket, ensuring that some files are older than 30 days (you may need to adjust your system's date temporarily for this or use old files).

2. Lambda IAM Role: - In the IAM dashboard, create a new role for Lambda.

   - Attach the `AmazonS3FullAccess` policy to this role. (Note: For enhanced security in real-world scenarios, use more restrictive permissions.)

3. Lambda Function: - Navigate to the Lambda dashboard and create a new function. - Choose Python 3.x as the runtime.

   - Assign the IAM role created in the previous step.

   - Write the Boto3 Python script to:   1. Initialize a boto3 S3 client.  2. List objects in the specified bucket.

     3. Delete objects older than 30 days. 4. Print the names of deleted objects for logging purposes.

4. Manual Invocation: - After saving your function, manually trigger it.

   - Go to the S3 dashboard and confirm that only files newer than 30 days remain.
Assignment 3: Monitor Unencrypted S3 Buckets Using AWS Lambda and Boto3

1. S3 Setup: - Navigate to the S3 dashboard and create a few buckets. Ensure that a couple of them don't have server-side encryption enabled.

2. Lambda IAM Role:  - In the IAM dashboard, create a new role for Lambda. - Attach the `AmazonS3ReadOnlyAccess` policy to this role.

3. Lambda Function: - Navigate to the Lambda dashboard and create a new function.  - Choose Python 3.x as the runtime.

   - Assign the IAM role created in the previous step. - Write the Boto3 Python script to:

     1. Initialize a boto3 S3 client. 2. List all S3 buckets.  3. Detect buckets without server-side encryption.

     4. Print the names of unencrypted buckets for logging purposes.

4. Manual Invocation:- After saving your function, manually trigger it.  - Review the Lambda logs to identify the buckets without server-side encryption.
Assignment 4: Automatic EBS Snapshot and Cleanup Using AWS Lambda and Boto3

1. EBS Setup:- Navigate to the EC2 dashboard and identify or create an EBS volume you wish to back up. - Note down the volume ID.

2. Lambda IAM Role: - In the IAM dashboard, create a new role for Lambda.  - Attach policies that allow Lambda to create EBS snapshots and delete them (`AmazonEC2FullAccess` for simplicity, but be more restrictive in real-world scenarios).

3. Lambda Function: - Navigate to the Lambda dashboard and create a new function.- Choose Python 3.x as the runtime. - Assign the IAM role created in the previous step.

   - Write the Boto3 Python script to:

     1. Initialize a boto3 EC2 client.  2. Create a snapshot for the specified EBS volume. 3. List snapshots and delete those older than 30 days. 4. Print the IDs of the created and deleted snapshots for logging purposes.

4. Event Source (Bonus): - Attach an event source, like Amazon CloudWatch Events, to trigger the Lambda function at your desired backup frequency (e.g., every week).

5. Manual Invocation: - After saving your function, either manually trigger it or wait for the scheduled event.
