### Problem Statement:

Managing AWS resources efficiently is crucial for cost optimization. One common challenge is the accumulation of unused or stale resources, such as Elastic Block Store (EBS) snapshots, over time. Identifying and cleaning up these resources manually can be time-consuming and error-prone, leading to unnecessary storage costs.

### Problem Solving - EBS Snapshot Cleanup:

**Objective:** The goal is to automate the identification and deletion of EBS snapshots that are not attached to any volumes or are no longer in use. By doing so, we aim to optimize storage costs in AWS.

### Steps to Implement EBS Snapshot Cleanup:

1. **Login to AWS Management Console:**
   - Open the [AWS Management Console](https://aws.amazon.com/console/).

2. **Create an EC2 Instance:**
   - Navigate to the EC2 service.
   - Launch a new EC2 instance, and by default, it will be attached to a volume.

3. **Create EBS Snapshots:**
   - Navigate to the EBS service.
   - Identify the volume attached to your EC2 instance.
   - Create snapshots for the volume.

4. **Create a Lambda Function:**
   - Navigate to the Lambda service.
   - Create a new Lambda function named "ebs-cost-optimization."
   - Provide a description (optional).

5. **Clone Repository and Add Code:**
   - Clone the GitHub repository containing the EBS snapshot cleanup code.
   - Open `lambda_function.py` and copy its contents.
   - Paste the code into the Lambda function's inline code editor.

6. **Configure Lambda Function:**
   - Set the function timeout (default is 3 seconds). Adjust based on your requirements.
   - Save the changes.

7. **IAM Role and Permissions:**
   - Navigate to the IAM service.
   - Locate the IAM role attached to the Lambda function.
   - Attach policies granting necessary permissions:
     - `ec2:DescribeSnapshots`
     - `ec2:DescribeInstances`
     - `ec2:DeleteSnapshot`

8. **Test Lambda Function:**
   - Manually test the Lambda function using the Lambda console.
   - Ensure it successfully identifies and deletes stale EBS snapshots.

9. **Schedule Cleanup Using CloudWatch Events:**
   - Navigate to the CloudWatch service.
   - Create a CloudWatch Events rule to trigger the Lambda function periodically.
   - Example schedule expression: `cron(0 0 * * ? *)` for daily execution.

10. **Monitor Using CloudWatch Logs:**
    - Monitor Lambda function logs in the CloudWatch Logs console.
    - Adjust log retention settings as needed.

### Conclusion:

By following these steps, you have implemented an automated solution for EBS snapshot cleanup, optimizing storage costs in your AWS environment. The Lambda function, triggered by CloudWatch Events, ensures regular and efficient management of EBS snapshots, addressing the problem of stale resources.
