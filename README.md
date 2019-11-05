# **Amazon S3 Security Settings and Controls**

© 2019 Amazon Web Services, Inc. and its affiliates. All rights reserved.
This sample code is made available under the MIT-0 license. See the LICENSE file.

Errors or corrections? Contact [mburbey@amazon.com](mailto:mburbey@amazon.com).
---
## Workshop Summary

In this workshop you will use IAM, S3 Bucket Policies, S3 Block Public Access and AWS Config to demonstrate multiple strategies for securing a S3 Bucket.

## Deploy AWS resources using CloudFormation

1. Click one of the launch links in the table below to deploy the resources using CloudFormation.  To avoid errors during deployment, select a region in which you have previously created AWS resources.

  | **Region Code** | **Region Name** | **Launch** |
  | --- | --- | --- |
  | us-west-1 | US West (N. California) | [Launch in us-west-1](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | us-west-2 | US West (Oregon) | [Launch in us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | us-east-1 | US East (N. Virginia) | [Launch in us-east-1](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | us-east-2 | US East (Ohio) | [Launch in us-east-2](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ca-central-1 | Canada (Central) | [Launch in ca-central-1](https://console.aws.amazon.com/cloudformation/home?region=ca-central-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | eu-central-1 | EU (Frankfurt) | [Launch in eu-central-1](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | eu-west-1 | EU (Ireland) | [Launch in eu-west-1](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | eu-west-2 | EU (London) | [Launch in eu-west-2](https://console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | eu-west-3 | EU (Paris) | [Launch in eu-west-3](https://console.aws.amazon.com/cloudformation/home?region=eu-west-3#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | eu-north-1 | EU (Stockholm) | [Launch in eu-north-1](https://console.aws.amazon.com/cloudformation/home?region=eu-north-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-east-1 | Asia Pacific (Hong Kong) | [Launch in ap-east-1](https://console.aws.amazon.com/cloudformation/home?region=ap-east-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-northeast-1 | Asia Pacific (Tokyo) | [Launch in ap-northeast-1](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-northeast-2 | Asia Pacific (Seoul) | [Launch in ap-northeast-2](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-northeast-3 | Asia Pacific (Osaka-Local) | [Launch in ap-northeast-3](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-3#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-southeast-1 | Asia Pacific (Singapore) | [Launch in ap-southeast-1](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-southeast-2 | Asia Pacific (Sydney) | [Launch in ap-southeast-2](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | ap-south-1 | Asia Pacific (Mumbai) | [Launch in ap-south-1](https://console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | me-south-1 | Middle East (Bahrain) | [Launch in me-south-1](https://console.aws.amazon.com/cloudformation/home?region=me-south-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |
  | sa-east-1 | South America (São Paulo) | [Launch in sa-east-1](https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=S3SecurityWorkshop&amp;templateURL=https://storage-specialists-cf-templates.s3-us-west-2.amazonaws.com/2019/s3_security.json) |

2. Click  **Next**  on the Create Stack page.
3. Click  **Next**.
4. Click  **Next**  Again. (skipping the Options and Advanced options sections)
5. On the Review page, scroll to the bottom and check the boxes to acknowledge that CloudFormation will create IAM resources, then click  **Create stack**.  

  ![](/images/mod1cf1.png)
6. Click **Events**. Events will not auto refresh.  You will need to manually refresh the page using the refresh button on the right side of the page.
7. Watch for **S3SecurityWorkshop** and a status of **CREATE_COMPLETE**

  ![](/images/cf_complete.png)
8. Click **Output**.  
9. Copy and paste the name of Bucket01 into a document on your computer.  

**Note:** Instances that are launched as part of this CloudFormation template may be in the initializing state for few minutes.

## Connect to the EC2 Instance using EC2 Instance Connect

1. From the AWS console, click  **Services**  and select  **EC2.**
2. Select  **Instances**  from the menu on the left.
3. Wait until the state of the S3_Workshop_Instance01 instance  shows as _running_ and all Status Checks have completed (i.e. **not** in _Initializing_ state).
4. Right-click on the **S3_Workshop_Instance01** instance and select  **Connect** from the menu.
5. From the dialog box, select the EC2 Instance Connect option, as shown below:

  ![](/images/mod1ssh1.png)

6. For the **User name** field, enter "ec2-user", then click **Connect**.

A new dialog box or tab on your browser should appear, providing you with a command line interface (CLI).  Keep this open - you will use the command line on the instance throughout this workshop.

**Note:**  The SSH session will disconnect after a period of inactivity.  If your session becomes unresponsive, close the window and repeat the steps above to reconnect.


## Setup AWS CLI

1. In the CLI for the instance, run the following commands to setup the AWS CLI

    $ aws configure

    Leave Access Key and Secret Key blank, set the region to the region you deployed your CloudFormation template in , output format leave default.

  ![](/images/aws_configure.png)  

2. Create a credentials file to be used by the AWS CLI.  This will allow you to switch between two different users easily.  

    $ cd ~/.aws  
    $ vi credentials  
Copy and paste the following credentials file template into your vi session.
```
[user1]
aws_access_key_id =
aws_secret_access_key =
[user2]
aws_access_key_id =
aws_secret_access_key =
```    
3. From the AWS console, click  **Services**  and select  **IAM.**  
4. Click **Users** in the left pane.  
5. Click **s3_security_lab_user1**.  
6. Click **Security credentials** tab.  
7. Click **Create access key**.  
8. Copy the Access key ID and Secret access key into the credentials file under User1.
9. Click **Close**.
10. Click **Users** in the left pane.
11. Click **s3_security_lab_user2**.
12. Click **Create access key**.  
13. Copy the Access key ID and Secret access key into the credentials file under User2.
14. Compare you credentials file to the one below and ensure your formatting is the same.  

  ![](/images/credentials.png)  

15. Save the file

## Exercise #1- Require HTTPS

In this exercise we will create a S3 Bucket Policy that requires connections to be secure.

1. From the AWS console, click  **Services**  and select  **S3.**
2. Click the bucket name. (Copied from CloudFormation Outputs previously.)
3. Click on the **Permissions** tab.  
4. Click **Bucket Policy**.  
5. Copy the bucket policy below and paste into the Bucket Policy Editor.
```
{
"Statement": [
{
   "Action": "s3:*",
   "Effect": "Deny",
   "Principal": "*",
   "Resource": "arn:aws:s3:::BUCKET_NAME/*",
   "Condition": {
       "Bool": {
        "aws:SecureTransport": false
        }
    }
    }
  ]
}
```

6. Replace BUCKET_NAME with the bucket name.  Sample bucket policy below.

  ![](/images/https_bucket_policy.png)

7. Click **Save**
8. In your SSH session run the following command. The command should return a 403 error since the endpoint-url is HTTP.

  $ aws s3api --endpoint-url http://s3.amazonaws.com --profile user1 head-object --key app1/file1 --bucket ${bucket}

9. In your SSH session run the following command. This command should succeed since it is using HTTPS.

  $ aws s3api --endpoint-url https://s3.amazonaws.com --profile user1 head-object --key app1/file1 --bucket ${bucket}

## Exercise #2- Require SSE-S3 Encryption

In this exercise we will create a S3 Bucket Policy that requires data at rest encryption.  We will also look at Default Encryption.

1. From the AWS console, click  **Services**  and select  **S3.**
2. Click the bucket name. (Copied from CloudFormation Outputs previously.)
3. Click on the **Permissions** tab.  
4. Click **Bucket Policy**.  
5. Click **Delete**, click **Delete** to confirm.  
6. Copy the bucket policy below and paste into the Bucket Policy Editor.
```
{
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringNotEquals": {
                    "s3:x-amz-server-side-encryption": "AES256"
                }
            }
        }
    ]
}
```
7. Replace BUCKET_NAME with the bucket name.  Sample bucket policy below.  

  ![](/images/sse_s3_bucket_policy.png)   
8. Click **Save**  
9. Go to your SSH session and create a small text file using the following command.
   $ cd ~  
  $ echo "123456789abcdefg" > textfile  
10. Attempt to PUT an object without encryption. The request should fail.
  $ aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
11. PUT an object using SSE-S3.  The request should succeed.
  $  aws s3api put-object --key text01 --body textfile --server-side-encryption AES256 --profile user1 --bucket ${bucket}  
12. From the AWS console, click  **Services**  and select  **S3.**  
13. Click the bucket name. (Copied from CloudFormation Outputs previously.)  
14. Click on the **Properties** tab.    
15. Default Encryption for AES-256(SSE-S3) is enabled.  

**Note**  
Bucket Policies are enforced based on how the request from the client is sent.  In this case the Bucket Policy denied the first attempt to PUT an object. Since Default Encryption is enabled the first attempt would have ended up encrypted anyway, however, Default Encryption doesn't override encryption flags.  For example, if Default Encryption is set to AWS-KMS and a request is sent with AES-256(SSE-S3) the request will be written as AES-256(SSE-S3).  Default Encryption behaves like a default not an override.  If a customer has a requirement that all objects have a certain type of encryption, then the only way to meet that requirement is with a bucket policy.

## Exercise #3- Block Public ACLs using Bucket Policy

In this exercise we will create a S3 Bucket Policy that prevents users from assigning public ACLs to objects.

1. From the AWS console, click  **Services**  and select  **S3.**
2. Click the bucket name. (Copied from CloudFormation Outputs previously.)
3. Click on the **Permissions** tab.  
4. Click **Bucket Policy**.  
5. Click **Delete**, click **Delete** to confirm.  
6. Copy the bucket policy below and paste into the Bucket Policy Editor.
```
{
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::BUCKET NAME/*",
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": "private"
                }
            }
        }
    ]
}
```
7. Replace BUCKET NAME with the bucket name.  Sample bucket policy below.
  ![](/images/block_public_acl_1.png)
8. Click **Save**  
9. Go to your SSH session, run the following command. The request should succeed since the default for an object ACL is private.  
  $ aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
10. Run the following command, the request will also succeed even though this isn’t the behavior we are expecting.  
  $ aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}  

**Note**  
The current bucket policy allows ACLs that are private but doesn't DENY anything.  It is important to write policies that prevent actions, not allow it when trying to restrict actions against a bucket. The current bucket policy also allows Public access to the bucket unintentionally due to the principal being a wildcard.  

10. Remove the existing bucket policy. Copy the bucket policy below and paste into the Bucket Policy Editor.
```
{
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": [
                    "s3:PutObject",
                    "s3:PutObjectAcl"
                    ],
            "Resource": "arn:aws:s3:::BUCKET NAME/*",
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": [
                           "public-read",
                           "public-read-write",
                           "authenticated-read"
                    ]
                }
            }
        }
    ]
}
```
11. Replace BUCKET NAME with the bucket name.  Sample bucket policy below.
  ![](/images/block_public_acl_2.png)
12. Click **Save**
13. Go to your SSH session, run the following command. The request should succeed since the default for an object ACL is private.  
  $ aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
14. Run the following command, the request should fail as the bucket policy will restrict the public-read ACL.  
  $ aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}

## Exercise #4- Configure S3 Block Public Access
In this exercise we will configure S3 Block Public Access, an easy way to prevent public access to your bucket.

1. From the AWS console, click  **Services**  and select  **S3.**
2. Click the bucket name. (Copied from CloudFormation Outputs previously.)
3. Click on the **Permissions** tab.  
4. Click **Bucket Policy**.  
5. Click **Delete**, click **Delete** to confirm.  
6. Click **Block public access**
7. Click **Edit**
8. Select **Block public access to buckets and objects granted through new access control lists (ACLs)**
![](/images/block_public_access_1.png)  

9. Click **Save**  

![](/images/block_public_access_2.png)  

10. Type **confirm**  
11. Click **Confirm**  
12. Go to your SSH session, run the following command. The request should succeed since the default for an object ACL is private.  
  $ aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
13. Run the following command, the request should fail as the bucket policy will restrict the public-read ACL.  
  $ aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}  
14. From the AWS console, click  **Services**  and select  **S3.**  
15. Click the bucket name. (Copied from CloudFormation Outputs previously.)  
16. Click on the **Permissions** tab.  
17. Click **Block public access**  
18. Click **Edit**  
19. Uncheck **Block public access to buckets and objects granted through new access control lists (ACLs)**  
![](/images/block_public_access_3.png)  
20. Click **Save**   
![](/images/block_public_access_2.png)  
21. Type **confirm**.  
22. Click **Confirm**.  

## Exercise #5- Restrict Access to a  S3 VPC Endpoint

In this exercise we will configure a S3 VPC Endpoint and a bucket policy to limit access to only requests that pass through the VPC Endpoint.  This is an easy way to limit access to only clients in your VPC.

1. In the AWS Console go to **VPC**.  
2. Click **Endpoints**.  
3. Click **Create Endpoint**.
4. Select the **S3** service name.
![](/images/vpc_endpoint_1.png)
5. Select the **S3SecurityWorkshopVPC** from the drop down menu.
![](/images/vpc_endpoint_2.png)
6. Do not select any route tables for now.  
![](/images/vpc_endpoint_3.png)
7. Leave Policy set to **Full Access**
![](/images/vpc_endpoint_4.png)
8. Click **Create endpoint**.
9. Click **Close**
10. Record the **Endpoint ID**.  
![](/images/vpc_endpoint_5.png)
12. From the AWS console, click  **Services**  and select  **S3.**
13. Click the bucket name. (Copied from CloudFormation Outputs previously.)
14. Click on the **Permissions** tab.  
14. Click **Bucket Policy**.  
15. Copy the bucket policy below and paste into the Bucket Policy Editor.
```
{
    "Statement": [
        {
            "Action": "s3:*",
            "Effect": "Deny",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringNotEquals": {
                    "aws:sourceVpce": "VPC_ENDPOINT_ID"
                }
            },
            "Principal": "*"
        }
    ]
}
```
16. Replace BUCKET_NAME with the bucket name and VPC_ENDPOINT_ID with the Endpoint ID.  Sample bucket policy below.  
![](/images/vpc_endpoint_6.png)
17. Click **Save**
18. Go to your SSH session, the request will fail since the S3 VPCE isn't associated with a route table.  
  $ aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
19. In the AWS Console go to **VPC**.  
20. Click **Endpoints**.  
21. The VPC Endpoint should be selected.  Select **Actions**, then click **Manage Route Tables**.
22. Select the Route Table that is associated with **S3SecurityWorkshopSubnet**
![](/images/vpc_endpoint_7.png)
23. Click **Modify Route Tables**
24. Go to your SSH session, run the following command. The request should now succeed.  
  $ aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
25. From the AWS console, click  **Services**  and select  **S3.**
26. Click the bucket name. (Copied from CloudFormation Outputs previously.)
27. Click on the **Permissions** tab.  
28. Click **Bucket Policy**.
29. Click **Delete**, click **Delete** to confirm.

##  Exercise #6- Use AWS Config to Detect a Public Bucket  

1. From the AWS console, click  **Services**  and select  **Config.**
2. If you haven't used AWS Config previously you will be brought to the Get started page.  If you have already used AWS Config jump to step
![](/images/config_4.png)
3. Go to bottom of page, under AWS Config role, select **Use an existing AWS Config service-linked role**.  
![](/images/config_6.png)
4. Click **Next**.
5. Click **Skip**.  
6. Click **Confirm**.  
**Note**  
If you receive an error regarding S3, AWS Config was used previously in another region.  Click **Previous**, **Previous**, under **Amazon S3 Bucket**, select **Choose a bucket from your account**.  Bucket name will start with config-bucket. Click **Next**, **Skip**, **Confirm**.  

![](/images/config_7.png)
7. Click **Rules**.  
8. Click **Add Rule**.
9. Filter rules by typing **S3** into search box.  
10. Click **s3_bucket_public_write_prohibited**.
11. Click **Save**.
12. The rule needs time to evaluate.  Refresh the page until you see **Compliant**.  
![](/images/config_5.png)
13. From the AWS console, click  **Services**  and select  **S3.**
14. Click the bucket name. (Copied from CloudFormation Outputs previously.)
15. Click on the **Permissions** tab.
16. Click on **Access Control List**.  
17. Under Public access, select **Everyone**.  
18. Check **Write objects** in the pop up window.
19. Click **Save**.  
![](/images/config_2.png)  
20. From the AWS console, click  **Services**  and select  **Config.**  
21. Click **Rules**.  
22. Click **s3_bucket_public_write_prohibited**.  
23. Click **Re-evaluate**.   
24. You will need to refresh the screen.  Your bucket should be **Noncompliant**.  
![](/images/config_3.png)
25. From the AWS console, click  **Services**  and select  **S3.**
26. Click the bucket name. (Copied from CloudFormation Outputs previously.)
27. Click on the **Permissions** tab.
28. Click on **Access Control List**.  
29. Under Public access, select **Everyone**.  
30. Unheck **Write objects** in the pop up window.
31. Click **Save**.  

## Exercise #7- Restrict Access to an IP Address

Create a S3 Bucket Policy that will restrict access to your S3 Bucket to only the IP address of the EC2 Instance.

## Exercise #8- Restrict Access to an IP Address and User Restrictions

Add to your S3 Bucket Policy from Exercise #7.  
s3_security_lab_user1 should only be able to read objects.  
s3_security_lab_user2 should be able to read and write objects.  

## Clean Up Resources

To ensurer you don't continue to be billed for services in your account from this workshop follow the steps below to remove all resources created ruing the workshop.

1. In your SSH session run the following command.  
  $ aws s3 rm s3://${bucket} --recursive  
2. From the AWS console, click  **Services**  and select  **Config.**  
2. Click **Rules**.  
3. Click **s3_bucket_public_write_prohibited**.
4. Click **Edit**.
5. Click **Delete Rule**.(Must scroll down)
6. Click **Delete**
7. In the AWS Console go to **VPC**.  
8. Click **Endpoints**.
9. Select the Endpoint created earlier, select **Actions**, click **Delete Endpoint**.  
10. Click **Yes,Delete**.
11. From the AWS console, click  **Services**  and select  **CloudFormation.**  
12. Select **S3SecurityWorkshop**.  
13. Click **Delete**.  
14. Click **Delete stack**.  
15. It will take a few minutes to delete everything.  Refresh the page to see an updated status.  **S3SecurityWorkshop** will be removed from the list if everything has been deleted correctly.
