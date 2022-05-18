# Security<a name="security-checks"></a>

You can use the following checks for the security category\.

**Note**  
If you enabled Security Hub for your AWS account, you can view your findings in the Trusted Advisor console\. For information, see [Viewing AWS Security Hub controls in AWS Trusted Advisor](security-hub-controls-with-trusted-advisor.md)\.  
You can view all controls in the AWS Foundational Security Best Practices security standard *except* for controls that have the **Category: Recover > Resilience**\. For a list of supported controls, see [AWS Foundational Security Best Practices controls](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-fsbp-controls.html) in the *AWS Security Hub User Guide*\.

**Contents**
+ [Amazon EC2 instances with Microsoft SQL Server end of support](#ec2-instances-with-sql-server-end-of-support)
+ [Amazon EBS Public Snapshots](#amazon-ebs-public-snapshots)
+ [Amazon RDS Public Snapshots](#amazon-rds-public-snapshots)
+ [Amazon RDS Security Group Access Risk](#amazon-rds-security-group-access-risk)
+ [Amazon Route 53 MX Resource Record Sets and Sender Policy Framework](#amazon-route-53-mx-resorc-resource-record-sets-sender-policy-framework)
+ [Amazon S3 Bucket Permissions](#amazon-s3-bucket-permissions)
+ [AWS CloudTrail Logging](#aws-cloudtrail-logging)
+ [AWS Lambda Functions Using Deprecated Runtimes](#aws-lambda-functions-deprecated-runtimes)
+ [AWS Well\-Architected high risk issues for security](#well-architected-high-risk-issues-security)
+ [CloudFront Custom SSL Certificates in the IAM Certificate Store](#cloudfront-custom-ssl-certificates-iam-certificate-store)
+ [CloudFront SSL Certificate on the Origin Server](#cloudfront-ssl-certificate-origin-server)
+ [ELB Listener Security](#elb-listener-security)
+ [ELB Security Groups](#elb-security-groups)
+ [Exposed Access Keys](#exposed-access-keys)
+ [IAM Access Key Rotation](#iam-access-key-rotation)
+ [IAM Password Policy](#iam-password-policy)
+ [IAM Use](#iam-use)
+ [MFA on Root Account](#mfa-root-account)
+ [Security Groups – Specific Ports Unrestricted](#security-groups-specific-ports-unrestricted)
+ [Security Groups – Unrestricted Access](#security-groups-unrestricted-access)

## Amazon EC2 instances with Microsoft SQL Server end of support<a name="ec2-instances-with-sql-server-end-of-support"></a>

**Description**  
Checks the SQL Server versions for Amazon Elastic Compute Cloud \(Amazon EC2\) instances running in the past 24 hours\. This check alerts you if the versions are near or have reached the end of support\. Each SQL Server version offers 10 years of support, including 5 years of mainstream support and 5 years of extended support\. After the end of support, the SQL Server version won’t receive regular security updates\. Running applications with unsupported SQL Server versions can bring security or compliance risks\.   
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Qsdfp3A4L3`

## Amazon EBS Public Snapshots<a name="amazon-ebs-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Elastic Block Store \(Amazon EBS\) volume snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`ePs02jT06w`

## Amazon RDS Public Snapshots<a name="amazon-rds-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Relational Database Service \(Amazon RDS\) DB snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`rSs93HQwa1`

## Amazon RDS Security Group Access Risk<a name="amazon-rds-security-group-access-risk"></a>

**Description**  
Checks security group configurations for Amazon Relational Database Service \(Amazon RDS\) and warns when a security group rule grants overly permissive access to your database\. The recommended configuration for a security group rule is to allow access only from specific Amazon Elastic Compute Cloud \(Amazon EC2\) security groups or from a specific IP address\. 

**Check ID**  
`nNauJisYIT`

## Amazon Route 53 MX Resource Record Sets and Sender Policy Framework<a name="amazon-route-53-mx-resorc-resource-record-sets-sender-policy-framework"></a>

**Description**  
For each MX resource record set, checks that the TXT or SPF resource record set contains a valid SPF record\. The record must start with "`v=spf1`"\. The SPF record specifies the servers that are authorized to send email for your domain, which helps detect and stop email address spoofing and to reduce spam\. Route 53 recommends that you use a TXT record instead of an SPF record\. Trusted Advisor reports this check as green as long as each MX resource record set has at least one SPF or TXT record\.

**Check ID**  
`c9D319e7sG`

## Amazon S3 Bucket Permissions<a name="amazon-s3-bucket-permissions"></a>

**Description**  
Checks buckets in Amazon Simple Storage Service \(Amazon S3\) that have open access permissions, or that allow access to any authenticated AWS user\.   
This check examines explicit bucket permissions, as well as bucket policies that might override those permissions\. Granting list access permissions to all users for an Amazon S3 bucket is not recommended\. These permissions can lead to unintended users listing objects in the bucket at high frequency, which can result in higher than expected charges\. Permissions that grant upload and delete access to everyone can lead to security vulnerabilities in your bucket\.

**Check ID**  
`Pfx0RwqBli`

## AWS CloudTrail Logging<a name="aws-cloudtrail-logging"></a>

**Description**  
Checks your use of AWS CloudTrail\. CloudTrail provides increased visibility into activity in your AWS account by recording information about AWS API calls made on the account\. You can use these logs to determine, for example, what actions a particular user has taken during a specified time period, or which users have taken actions on a particular resource during a specified time period\.   
Because CloudTrail delivers log files to an Amazon Simple Storage Service \(Amazon S3\) bucket, CloudTrail must have write permissions for the bucket\. If a trail applies to all Regions \(the default when creating a new trail\), the trail appears multiple times in the Trusted Advisor report\.

**Check ID**  
`vjafUGJ9H0`

## AWS Lambda Functions Using Deprecated Runtimes<a name="aws-lambda-functions-deprecated-runtimes"></a>

**Description**  
Checks for Lambda functions that are configured to use a runtime that is approaching deprecation, or is deprecated\. Deprecated runtimes are not eligible for security updates or technical support\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q4C5`

## AWS Well\-Architected high risk issues for security<a name="well-architected-high-risk-issues-security"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the security pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L3`

## CloudFront Custom SSL Certificates in the IAM Certificate Store<a name="cloudfront-custom-ssl-certificates-iam-certificate-store"></a>

**Description**  
Checks the SSL certificates for CloudFront alternate domain names in the IAM certificate store\. This check alerts you if a certificate is expired, will expire soon, uses outdated encryption, or is not configured correctly for the distribution\.   
When a custom certificate for an alternate domain name expires, browsers that display your CloudFront content might show a warning message about the security of your website\. Certificates that are encrypted by using the SHA\-1 hashing algorithm are being deprecated by web browsers such as Chrome and Firefox\. A certificate must contain a domain name that matches either the Origin Domain Name or the domain name in the host header of a viewer request\. If it doesn't match, CloudFront returns an HTTP status code of 502 \(bad gateway\) to the user\.   
For more information, see [Using Alternate Domain Names and HTTPS](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html#CNAMEsAndHTTPS)\.

**Check ID**  
`N425c450f2`

## CloudFront SSL Certificate on the Origin Server<a name="cloudfront-ssl-certificate-origin-server"></a>

**Description**  
Checks your origin server for SSL certificates that are expired, about to expire, missing, or that use outdated encryption\. If a certificate has one of these issues, CloudFront responds to requests for your content with HTTP status code 502, Bad Gateway\.

**Check ID**  
`N430c450f2`

## ELB Listener Security<a name="elb-listener-security"></a>

**Description**  
Checks for load balancers with listeners that do not use recommended security configurations for encrypted communication\. AWS recommends using a secure protocol \(HTTPS or SSL\), up\-to\-date security policies, as well as ciphers and protocols that are secure\.  
When you use a secure protocol for a front\-end connection \(client to load balancer\), the requests are encrypted between your clients and the load balancer, which create a more secure environment\. Elastic Load Balancing provides predefined security policies with ciphers and protocols that adhere to AWS security best practices\. New versions of predefined policies are released as new configurations become available\.

**Check ID**  
`a2sEc6ILx`

## ELB Security Groups<a name="elb-security-groups"></a>

**Description**  
Checks for load balancers configured with a missing security group, or a security group that allows access to ports that are not configured for the load balancer\.   
If a security group associated with a load balancer is deleted, the load balancer will not work as expected\. If a security group allows access to ports that are not configured for the load balancer, the risk of loss of data or malicious attacks increases\.

**Check ID**  
`xSqX82fQu`

## Exposed Access Keys<a name="exposed-access-keys"></a>

**Description**  
Checks popular code repositories for access keys that have been exposed to the public\. This also checks for irregular Amazon Elastic Compute Cloud \(Amazon EC2\) usage that could be the result of a compromised access key\.   
An access key consists of an access key ID and the corresponding secret access key\. Exposed access keys pose a security risk to your account and other users, could lead to excessive charges from unauthorized activity or abuse, and violate the [AWS Customer Agreement](http://aws.amazon.com/agreement)\.   
If your access key is exposed, take immediate action to secure your account\. To protect your account from excessive charges, AWS temporarily limits your ability to create some AWS resources\. This does not make your account secure\. It only partially limits the unauthorized usage for which you could be charged\.  
This check doesn't guarantee the identification of exposed access keys or compromised EC2 instances\. You are ultimately responsible for the safety and security of your access keys and AWS resources\.
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`12Fnkpl8Y5`

## IAM Access Key Rotation<a name="iam-access-key-rotation"></a>

**Description**  
Checks for active IAM access keys that have not been rotated in the last 90 days\.   
When you rotate your access keys regularly, you reduce the chance that a compromised key could be used without your knowledge to access resources\. For the purposes of this check, the last rotation date and time is when the access key was created or most recently activated\. The access key number and date come from the `access_key_1_last_rotated` and `access_key_2_last_rotated` information in the most recent IAM credential report\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`DqdJqYeRm5`

## IAM Password Policy<a name="iam-password-policy"></a>

**Description**  
Checks the password policy for your account and warns when a password policy is not enabled, or if password content requirements have not been enabled\.   
Password content requirements increase the overall security of your AWS environment by enforcing the creation of strong user passwords\. When you create or change a password policy, the change is enforced immediately for new users but does not require existing users to change their passwords\.

**Check ID**  
`Yw2K9puPzl`

## IAM Use<a name="iam-use"></a>

**Description**  
Checks for your use of IAM\. You can use IAM to create users, groups, and roles in AWS\. You can also use permissions to control access to AWS resources\. This check is intended to discourage the use of root access by checking for existence of at least one IAM user\.

**Check ID**  
`zXCkfM1nI3`

## MFA on Root Account<a name="mfa-root-account"></a>

**Description**  
Checks the root account and warns if multi\-factor authentication \(MFA\) is not enabled\.   
For increased security, we recommend that you protect your account by using MFA, which requires a user to enter a unique authentication code from their MFA hardware or virtual device when interacting with the AWS Management Console and associated websites\.

**Check ID**  
`7DAFEmoDos`

## Security Groups – Specific Ports Unrestricted<a name="security-groups-specific-ports-unrestricted"></a>

**Description**  
Checks security groups for rules that allow unrestricted access \(0\.0\.0\.0/0\) to specific ports\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\. The ports with highest risk are flagged red, and those with less risk are flagged yellow\. Ports flagged green are typically used by applications that require unrestricted access, such as HTTP and SMTP\.  
If you have intentionally configured your security groups in this manner, we recommend using additional security measures to secure your infrastructure \(such as IP tables\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`HCP4007jGY`

## Security Groups – Unrestricted Access<a name="security-groups-unrestricted-access"></a>

**Description**  
Checks security groups for rules that allow unrestricted access to a resource\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`1iG5NDGVre`