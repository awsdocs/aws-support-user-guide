# Security<a name="security-checks"></a>

You can use the following checks for the security category\.

**Note**  
If you enabled Security Hub for your AWS account, you can view your findings in the Trusted Advisor console\. For information, see [Viewing AWS Security Hub controls in AWS Trusted Advisor](security-hub-controls-with-trusted-advisor.md)\.  
You can view all controls in the AWS Foundational Security Best Practices security standard *except* for controls that have the **Category: Recover > Resilience**\. For a list of supported controls, see [AWS Foundational Security Best Practices controls](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-fsbp-controls.html) in the *AWS Security Hub User Guide*\.

**Contents**
+ [Amazon EC2 instances with Microsoft SQL Server end of support](#ec2-instances-with-sql-server-end-of-support)
+ [Amazon EC2 instances with Microsoft Windows Server end of support](#ec2-instances-with-windows-server-end-of-support)
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

**Alert Criteria**  
+ Red: An EC2 instance has an SQL Server version that reached the end of support\.
+ Yellow: An EC2 instance has an SQL Server version that will reach the end of support in 12 months\.

**Recommended Action**  
To modernize your SQL Server workloads, consider refactoring to AWS Cloud native databases like Amazon Aurora\. For more information, see [Modernize Windows Workloads with AWS](http://aws.amazon.com/windows/modernization/)\.  
 To move to a fully managed database, consider replatforming to Amazon Relational Database Service \(Amazon RDS\)\. For more information, see [Amazon RDS for SQL Server](http://aws.amazon.com/rds/sqlserver/)\.  
To upgrade your SQL Server on Amazon EC2, consider using the automation runbook to simplify your upgrade\. For more information, see the [AWS Systems Manager documentation](https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awsec2-CloneInstanceAndUpgradeSQLServer.html)\.  
 If you can’t upgrade your SQL Server on Amazon EC2, consider the End\-of\-Support Migration Program \(EMP\) for Windows Server\. For more information, see the [EMP Website](http://aws.amazon.com/emp-windows-server/)\.

**Additional Resources**  
+ [Get ready for SQL Server end of support with AWS](http://aws.amazon.com/sql/sql2008-eos/)
+ [Microsoft SQL Server on AWS](http://aws.amazon.com/sql)

**Report columns**  
+ Status
+ Region
+ Instance ID
+ SQL Server Version
+ Support Cycle
+ End of Support
+ Last Updated Time

## Amazon EC2 instances with Microsoft Windows Server end of support<a name="ec2-instances-with-windows-server-end-of-support"></a>

**Description**  
This check alerts you if the versions are near or have reached the end of support\. Each Windows Server version offers 10 years of support\. This includes 5 years of mainstream support and 5 years of extended support\. After the end of support, the Windows Server version won’t receive regular security updates\. If you run applications with unsupported Windows Server versions, you risk the security or compliance of these applications\.

**Check ID**  
`Qsdfp3A4L4`

**Alert Criteria**  
+ Red: An EC2 instance has a Windows Server version that reached the end of support \(Windows Server 2003, 2003 R2, 2008, and 2008 R2\)\.
+ Yellow: An EC2 instance has a Windows Server version that will reach the end of support in less than 18 months \(Windows Server 2012 and 2012 R2\)\.

**Recommended Action**  
To modernize your Windows Server workloads, consider the various options available on [Modernize Windows Workloads with AWS](http://aws.amazon.com/windows/modernization/)\.  
To upgrade your Windows Server workloads to run on more recent versions of Windows Server, you can use an automation runbook\. For more information, see the [AWS Systems Manager documentation](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/os-inplaceupgrade.html)\.  
If you can’t upgrade your Windows Server workloads because of application incompatibilities, consider the End\-of\-Support Migration Program \(EMP\) for Windows Server\. For more information, see the [EMP Website](http://aws.amazon.com/emp-windows-server/)\. You can also purchase Extended Security Updates \(ESU\) from Microsoft for a maximum of 3 years after the end of support date for a product\. [Learn more](http://aws.amazon.com/windows/faq/#eos-microsoft-products)\.

**Additional Resources**  
+ [Windows on AWS](http://aws.amazon.com/windows/?blog-posts-content-windows.sort-by=item.additionalFields.createdDate=desc)
+ [End\-of\-Support Migration Program for Windows Server](http://aws.amazon.com/emp-windows-server/)

**Report columns**  
+ Status
+ Region
+ Instance ID
+ Windows Server Version
+ Support Cycle
+ End of Support
+ Last Updated Time

## Amazon EBS Public Snapshots<a name="amazon-ebs-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Elastic Block Store \(Amazon EBS\) volume snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`ePs02jT06w`

**Alert Criteria**  
Red: The EBS volume snapshot is marked as public\.

**Recommended Action**  
Unless you are certain you want to share all the data in the snapshot with all AWS accounts and users, modify the permissions: mark the snapshot as private, and then specify the accounts that you want to give permissions to\. For more information, see [Sharing an Amazon EBS Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-modifying-snapshot-permissions.html)\. This check can't be excluded from view in the Trusted Advisor console\.  
To modify permissions for your snapshots directly, you can use a runbook in the AWS Systems Manager console\. For more information, see [https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-modifyebssnapshotpermission.html](https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-modifyebssnapshotpermission.html)\.

**Additional Resources**  
[Amazon EBS Snapshots](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html)

**Report columns**  
+ Status
+ Region
+ Volume ID
+ Snapshot ID
+ Description

## Amazon RDS Public Snapshots<a name="amazon-rds-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Relational Database Service \(Amazon RDS\) DB snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`rSs93HQwa1`

**Alert Criteria**  
Red: The Amazon RDS snapshot is marked as public\.

**Recommended Action**  
Unless you are certain you want to share all the data in the snapshot with all AWS accounts and users, modify the permissions: mark the snapshot as private, and then specify the accounts that you want to give permissions to\. For more information, see [Sharing a DB Snapshot or DB Cluster Snapshot](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ShareSnapshot.html)\. This check can't be excluded from view in the Trusted Advisor console\.  
To modify permissions for your snapshots directly, you can use a runbook in the AWS Systems Manager console\. For more information, see [https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-modifyrdssnapshotpermission.html](https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-modifyrdssnapshotpermission.html)\.

**Additional Resources**  
[Backing Up and Restoring Amazon RDS DB Instances](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html)

**Report columns**  
+ Status
+ Region
+ DB Instance or Cluster ID
+ Snapshot ID

## Amazon RDS Security Group Access Risk<a name="amazon-rds-security-group-access-risk"></a>

**Description**  
Checks security group configurations for Amazon Relational Database Service \(Amazon RDS\) and warns when a security group rule grants overly permissive access to your database\. The recommended configuration for a security group rule is to allow access only from specific Amazon Elastic Compute Cloud \(Amazon EC2\) security groups or from a specific IP address\. 

**Check ID**  
`nNauJisYIT`

**Alert Criteria**  
+ Yellow: A DB security group rule references an Amazon EC2 security group that grants global access on one of these ports: 20, 21, 22, 1433, 1434, 3306, 3389, 4333, 5432, 5500\. 
+ Yellow: A DB security group rule grants access to more than a single IP address \(the CIDR rule suffix is not /0 or /32\)\. 
+ Red: A DB security group rule grants global access \(the CIDR rule suffix is /0\)\.

**Recommended Action**  
Review your security group rules and restrict access to authorized IP addresses or IP ranges\. To edit a security group, use the [AuthorizeDBSecurityGroupIngress](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_AuthorizeDBSecurityGroupIngress.html) API or the AWS Management Console\. For more information, see [Working with DB Security Groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithSecurityGroups.html)\. 

**Additional Resources**  
+ [Amazon RDS Security Groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html)
+ [Classless Inter\-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)
+ [List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

**Report columns**  
+ Status
+ Region
+ RDS Security Group Name
+ Ingress Rule
+ Reason

## Amazon Route 53 MX Resource Record Sets and Sender Policy Framework<a name="amazon-route-53-mx-resorc-resource-record-sets-sender-policy-framework"></a>

**Description**  
For each MX resource record set, checks that the TXT or SPF resource record set contains a valid SPF record\. The record must start with "`v=spf1`"\. The SPF record specifies the servers that are authorized to send email for your domain, which helps detect and stop email address spoofing and to reduce spam\. Route 53 recommends that you use a TXT record instead of an SPF record\. Trusted Advisor reports this check as green as long as each MX resource record set has at least one SPF or TXT record\.

**Check ID**  
`c9D319e7sG`

**Alert Criteria**  
Yellow: An MX resource record set doesn’t have a TXT or SPF resource record that contains a valid SPF value\. 

**Recommended Action**  
For each MX resource record set, create a TXT resource record set that contains a valid SPF value\. For more information, see [Sender Policy Framework: SPF Record Syntax](http://www.open-spf.org/SPF_Record_Syntax) and [Creating Resource Record Sets By Using the Amazon Route 53 Console](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/RRSchanges_console.html)\. 

**Additional Resources**  
+ [Sender Policy Framework](http://en.wikipedia.org/wiki/Sender_Policy_Framework)
+ [MX record](http://en.wikipedia.org/wiki/MX_record)

**Report columns**  
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Status

## Amazon S3 Bucket Permissions<a name="amazon-s3-bucket-permissions"></a>

**Description**  
Checks buckets in Amazon Simple Storage Service \(Amazon S3\) that have open access permissions, or that allow access to any authenticated AWS user\.   
This check examines explicit bucket permissions, as well as bucket policies that might override those permissions\. Granting list access permissions to all users for an Amazon S3 bucket is not recommended\. These permissions can lead to unintended users listing objects in the bucket at high frequency, which can result in higher than expected charges\. Permissions that grant upload and delete access to everyone can lead to security vulnerabilities in your bucket\.

**Check ID**  
`Pfx0RwqBli`

**Alert Criteria**  
+ Yellow: The bucket ACL allows List access for **Everyone** or **Any Authenticated AWS User**\.
+ Yellow: A bucket policy allows any kind of open access\.
+  Yellow: Bucket policy has statements that grant public access\. The **Block public and cross\-account access to buckets that have public policies** setting is turned on and has restricted access to only authorized users of that account until public statements are removed\.
+ Yellow: Trusted Advisor does not have permission to check the policy, or the policy could not be evaluated for other reasons\.
+ Red: The bucket ACL allows upload and delete access for **Everyone** or **Any Authenticated AWS User**\.

**Recommended Action**  
If a bucket allows open access, determine if open access is truly needed\. If not, update the bucket permissions to restrict access to the owner or specific users\. Use Amazon S3 Block Public Access to control the settings that allow public access to your data\. See [Setting Bucket and Object Access Permissions](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/set-permissions.html)\.

**Additional Resources**  
[Managing Access Permissions to Your Amazon S3 Resources](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html)

**Report columns**  
+ Status
+ Region Name
+ Region API Parameter
+ Bucket Name
+ ACL Allows List
+ ACL Allows Upload/Delete
+ Policy Allows Access

## AWS CloudTrail Logging<a name="aws-cloudtrail-logging"></a>

**Description**  
Checks your use of AWS CloudTrail\. CloudTrail provides increased visibility into activity in your AWS account by recording information about AWS API calls made on the account\. You can use these logs to determine, for example, what actions a particular user has taken during a specified time period, or which users have taken actions on a particular resource during a specified time period\.   
Because CloudTrail delivers log files to an Amazon Simple Storage Service \(Amazon S3\) bucket, CloudTrail must have write permissions for the bucket\. If a trail applies to all Regions \(the default when creating a new trail\), the trail appears multiple times in the Trusted Advisor report\.

**Check ID**  
`vjafUGJ9H0`

**Alert Criteria**  
+ Yellow: CloudTrail reports log delivery errors for a trail\.
+ Red: A trail has not been created for a Region, or logging is turned off for a trail\.

**Recommended Action**  
To create a trail and start logging from the console, go to the [AWS CloudTrail console](https://console.aws.amazon.com/cloudtrail/home)\.   
To start logging, see [Stopping and Starting Logging for a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/create_trail_using_cli.html#stopstartclil)\.   
If you receive log delivery errors, check to make sure that the bucket exists and that the necessary policy is attached to the bucket\. See [Amazon S3 Bucket Policy](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/create_trail_bucket_policy.html)\. 

**Additional Resources**  
+ [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)
+ [Supported Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/what_is_cloud_trail_supported_regions.html)
+ [Supported Services](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/what_is_cloud_trail_supported_services.html)

**Report columns**  
+ Status
+ Region
+ Trail Name
+ Logging Status
+ Bucket Name
+ Last Delivery Date

## AWS Lambda Functions Using Deprecated Runtimes<a name="aws-lambda-functions-deprecated-runtimes"></a>

**Description**  
Checks for Lambda functions that are configured to use a runtime that is approaching deprecation, or is deprecated\. Deprecated runtimes are not eligible for security updates or technical support\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.
Published Lambda function versions are immutable, which means they can be invoked but not updated\. Only the `$LATEST` version for a Lambda function can be updated\. For more information, see [Lambda function versions](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html)\.

**Check ID**  
`L4dfs2Q4C5`

**Alert Criteria**  
+ Red: The function is running on a runtime that is already deprecated\. 
+ Yellow: The function is running on a runtime that will be deprecated within 120 days\.

**Recommended Action**  
If you have functions that are running on a runtime that is approaching deprecation, you should prepare for migration to a supported runtime\. For more information, see [Runtime support policy](https://docs.aws.amazon.com/lambda/latest/dg/runtime-support-policy.html)\.  
We recommend that you delete earlier function versions that you’re no longer using\.

**Additional Resources**  
[Lambda runtimes](https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html)

**Report columns**  
+ Status
+ Region
+ Function ARN
+ Runtime
+ Days to Deprecation
+ Deprecation Date
+ Average Daily Invokes
+ Last Updated Time

## AWS Well\-Architected high risk issues for security<a name="well-architected-high-risk-issues-security"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the security pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L3`

**Alert Criteria**  
+ Red: At least one active high risk issue was identified in the security pillar for AWS Well\-Architected\.
+ Green: No active high risk issues were detected in the security pillar for AWS Well\-Architected\.

**Recommended Action**  
AWS Well\-Architected detected high risk issues during your workload evaluation\. These issues present opportunities to reduce risk and save money\. Sign in to the [AWS Well\-Architected](https://console.aws.amazon.com/wellarchitected) tool to review your answers and take action to resolve your active issues\.

**Report columns**  
+ Status
+ Region
+ Workload ARN
+ Workload Name
+ Reviewer Name
+ Workload Type
+ Workload Started Date
+ Workload Last Modified Date
+ Number of identified HRIs for Security
+ Number of HRIs resolved for Security
+ Number of questions for Security
+ Total number of questions in Security pillar
+ Last Updated Time

## CloudFront Custom SSL Certificates in the IAM Certificate Store<a name="cloudfront-custom-ssl-certificates-iam-certificate-store"></a>

**Description**  
Checks the SSL certificates for CloudFront alternate domain names in the IAM certificate store\. This check alerts you if a certificate is expired, will expire soon, uses outdated encryption, or is not configured correctly for the distribution\.   
When a custom certificate for an alternate domain name expires, browsers that display your CloudFront content might show a warning message about the security of your website\. Certificates that are encrypted by using the SHA\-1 hashing algorithm are being deprecated by web browsers such as Chrome and Firefox\.   
A certificate must contain a domain name that matches either the Origin Domain Name or the domain name in the host header of a viewer request\. If it doesn't match, CloudFront returns an HTTP status code of 502 \(bad gateway\) to the user\. For more information, see [Using Alternate Domain Names and HTTPS](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html#CNAMEsAndHTTPS)\.

**Check ID**  
`N425c450f2`

**Alert Criteria**  
+ Red: A custom SSL certificate is expired\.
+ Yellow: A custom SSL certificate expires in the next seven days\.
+ Yellow: A custom SSL certificate was encrypted by using the SHA\-1 hashing algorithm\.
+ Yellow: One or more of the alternate domain names in the distribution don't appear either in the Common Name field or the Subject Alternative Names field of the custom SSL certificate\.

**Recommended Action**  
Renew an expired certificate or a certificate that is about to expire\.  
Replace a certificate that was encrypted by using the SHA\-1 hashing algorithm with a certificate that is encrypted by using the SHA\-256 hashing algorithm\.  
Replace the certificate with a certificate that contains the applicable values in the Common Name or Subject Alternative Domain Names fields\.

**Additional Resources**  
[Using an HTTPS Connection to Access Your Objects](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html)

**Report columns**  
+ Status
+ Distribution ID
+ Distribution Domain Name
+ Certificate Name
+ Reason

## CloudFront SSL Certificate on the Origin Server<a name="cloudfront-ssl-certificate-origin-server"></a>

**Description**  
Checks your origin server for SSL certificates that are expired, about to expire, missing, or that use outdated encryption\. If a certificate has one of these issues, CloudFront responds to requests for your content with HTTP status code 502, Bad Gateway\.  
Certificates that were encrypted by using the SHA\-1 hashing algorithm are being deprecated by web browsers such as Chrome and Firefox\. Depending on the number of SSL certificates that you have associated with your CloudFront distributions, this check might add a few cents per month to your bill with your web hosting provider, for example, AWS if you're using Amazon EC2 or Elastic Load Balancing as the origin for your CloudFront distribution\. This check does not validate your origin certificate chain or certificate authorities\. You can check these in your CloudFront configuration\. 

**Check ID**  
`N430c450f2`

**Alert Criteria**  
+ Red: An SSL certificate on your origin has expired or is missing\.
+ Yellow: An SSL certificate on your origin expires in the next thirty days\.
+ Yellow: An SSL certificate on your origin was encrypted by using the SHA\-1 hashing algorithm\.
+ Yellow: An SSL certificate on your origin can't be located\. The connection might have failed due to timeout, or other HTTPS connection problems\.

**Recommended Action**  
Renew the certificate on your origin if it has expired or is about to expire\.  
Add a certificate if one does not exist\.  
Replace a certificate that was encrypted by using the SHA\-1 hashing algorithm with a certificate that is encrypted by using the SHA\-256 hashing algorithm\.

**Additional Resources**  
[Using Alternate Domain Names and HTTPS](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html#CNAMEsAndHTTPS)

**Report columns**  
+ Status
+ Distribution ID
+ Distribution Domain Name
+ Origin
+ Reason

## ELB Listener Security<a name="elb-listener-security"></a>

**Description**  
Checks for load balancers with listeners that do not use recommended security configurations for encrypted communication\. AWS recommends using a secure protocol \(HTTPS or SSL\), up\-to\-date security policies, as well as ciphers and protocols that are secure\.  
When you use a secure protocol for a front\-end connection \(client to load balancer\), the requests are encrypted between your clients and the load balancer, which create a more secure environment\. Elastic Load Balancing provides predefined security policies with ciphers and protocols that adhere to AWS security best practices\. New versions of predefined policies are released as new configurations become available\.

**Check ID**  
`a2sEc6ILx`

**Alert Criteria**  
+ Yellow: A load balancer has no listener that uses a secure protocol \(HTTPS or SSL\)\.
+ Yellow: A load balancer listener uses an outdated predefined SSL security policy\.
+ Yellow: A load balancer listener uses a cipher or protocol that is not recommended\.
+  Red: A load balancer listener uses an insecure cipher or protocol\.

**Recommended Action**  
If the traffic to your load balancer must be secure, use either the HTTPS or the SSL protocol for the front\-end connection\.  
Upgrade your load balancer to the latest version of the predefined SSL security policy\.  
Use only the recommended ciphers and protocols\.  
For more information, see [Listener Configurations for Elastic Load Balancing](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/elb-listener-config.html)\.

**Additional Resources**  
+ [Listener Configurations Quick Reference](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/using-elb-listenerconfig-quickref.html)
+ [Update SSL Negotiation Configuration of Your Load Balancer](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/ssl-config-update.html)
+ [SSL Negotiation Configurations for Elastic Load Balancing](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/elb-ssl-security-policy.html)
+ [SSL Security Policy Table](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/elb-security-policy-table.html)

**Report columns**  
+ Status
+ Region
+ Load Balancer Name
+ Load Balancer Port
+ Reason

## ELB Security Groups<a name="elb-security-groups"></a>

**Description**  
Checks for load balancers configured with a missing security group, or a security group that allows access to ports that are not configured for the load balancer\.   
If a security group associated with a load balancer is deleted, the load balancer will not work as expected\. If a security group allows access to ports that are not configured for the load balancer, the risk of loss of data or malicious attacks increases\.

**Check ID**  
`xSqX82fQu`

**Alert Criteria**  
+ Yellow: The inbound rules of an Amazon VPC security group associated with a load balancer allow access to ports that are not defined in the load balancer's listener configuration\. 
+ Red: A security group associated with a load balancer does not exist\. 

**Recommended Action**  
Configure the security group rules to restrict access to only those ports and protocols that are defined in the load balancer listener configuration, plus the ICMP protocol to support Path MTU Discovery\. See [Listeners for Your Classic Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-listener-config.html) and [Security Groups for Load Balancers in a VPC](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-groups.html#elb-vpc-security-groups)\.  
If a security group is missing, apply a new security group to the load balancer\. Create security group rules that restrict access to only those ports and protocols that are defined in the load balancer listener configuration\. See [Security Groups for Load Balancers in a VPC](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-groups.html#elb-vpc-security-groups)\. 

**Additional Resources**  
+ [Elastic Load Balancing User Guide](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)
+ [Configure Your Classic Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-configure-load-balancer.html)

**Report columns**  
+ Status
+ Region
+ Load Balancer Name
+ Security Group IDs
+ Reason

## Exposed Access Keys<a name="exposed-access-keys"></a>

**Description**  
Checks popular code repositories for access keys that have been exposed to the public and for irregular Amazon Elastic Compute Cloud \(Amazon EC2\) usage that could be the result of a compromised access key\.   
An access key consists of an access key ID and the corresponding secret access key\. Exposed access keys pose a security risk to your account and other users, could lead to excessive charges from unauthorized activity or abuse, and violate the [AWS Customer Agreement](http://aws.amazon.com/agreement)\.   
If your access key is exposed, take immediate action to secure your account\. To protect your account from excessive charges, AWS temporarily limits your ability to create some AWS resources\. This does not make your account secure\. It only partially limits the unauthorized usage for which you could be charged\.  
This check doesn't guarantee the identification of exposed access keys or compromised EC2 instances\. You are ultimately responsible for the safety and security of your access keys and AWS resources\.
 If a deadline is shown for an access key, AWS may suspend your AWS account if the unauthorized usage is not stopped by that date\. If you believe an alert is in error, [contact AWS Support](https://console.aws.amazon.com/support/home?#/case/create?issueType=customer-service&serviceCode=customer-account&categoryCode=security)\.  
The information displayed in Trusted Advisor might not reflect the most recent state of your account\. No exposed access keys are marked as resolved until all exposed access keys on the account have been resolved\. This data synchronization can take up to one week\.

**Check ID**  
`12Fnkpl8Y5`

**Alert Criteria**  
+ Red: Potentially compromised – AWS has identified an access key ID and corresponding secret access key that have been exposed on the Internet and may have been compromised \(used\)\.
+ Red: Exposed – AWS has identified an access key ID and corresponding secret access key that have been exposed on the Internet\.
+ Red: Suspected \- Irregular Amazon EC2 usage indicates that an access key may have been compromised, but it has not been identified as exposed on the Internet\.

**Recommended Action**  
Delete the affected access key as soon as possible\. If the key is associated with an IAM user, see [Managing Access Keys for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/ManagingCredentials.html)\.  
Check your account for unauthorized usage\. Sign in to the [AWS Management Console](https://console.aws.amazon.com/) and check each service console for suspicious resources\. Pay special attention to running Amazon EC2 instances, Spot Instance requests, access keys, and IAM users\. You can also check overall usage on the [Billing and Cost Management console](https://console.aws.amazon.com/billing/home#/)\.

**Additional Resources**  
+ [Best Practices for Managing AWS Access Keys](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html)
+ [AWS Security Audit Guidelines](https://docs.aws.amazon.com/general/latest/gr/aws-security-audit-guide.html)

**Report columns**  
+ Access Key ID
+ User Name \(IAM or Root\)
+ Fraud Type
+ Case ID
+ Time Updated
+ Location
+ Deadline
+ Usage \(USD per Day\)

## IAM Access Key Rotation<a name="iam-access-key-rotation"></a>

**Description**  
Checks for active IAM access keys that have not been rotated in the last 90 days\.   
When you rotate your access keys regularly, you reduce the chance that a compromised key could be used without your knowledge to access resources\. For the purposes of this check, the last rotation date and time is when the access key was created or most recently activated\. The access key number and date come from the `access_key_1_last_rotated` and `access_key_2_last_rotated` information in the most recent IAM credential report\.  
Because the regeneration frequency of a credential report is restricted, refreshing this check might not reflect recent changes\. For more information, see [Getting Credential Reports for Your AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html)\.  
In order to create and rotate access keys, a user must have the appropriate permissions\. For more information, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_delegate-permissions_examples.html#creds-policies-credentials)\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`DqdJqYeRm5`

**Alert Criteria**  
+ Green: The access key is active and has been rotated in the last 90 days\.
+ Yellow: The access key is active and has been rotated in the last 2 years, but more than 90 days ago\.
+ Red: The access key is active and has not been rotated in the last 2 years\.

**Recommended Action**  
 Rotate access keys on a regular basis\. See [Rotating Access Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_RotateAccessKey) and [Managing Access Keys for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)\.

**Additional Resources**  
+ [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
+ [How to rotate access keys for IAM users](http://aws.amazon.com/blogs/security/how-to-rotate-access-keys-for-iam-users/)

**Report columns**  
+ Status
+ IAM user
+ Access Key
+ Key Last Rotated
+ Reason

## IAM Password Policy<a name="iam-password-policy"></a>

**Description**  
Checks the password policy for your account and warns when a password policy is not enabled, or if password content requirements have not been enabled\.   
Password content requirements increase the overall security of your AWS environment by enforcing the creation of strong user passwords\. When you create or change a password policy, the change is enforced immediately for new users but does not require existing users to change their passwords\.

**Check ID**  
`Yw2K9puPzl`

**Alert Criteria**  
+ Yellow: A password policy is enabled, but at least one content requirement is not enabled\. 
+ Red: No password policy is enabled\. 

**Recommended Action**  
If some content requirements are not enabled, consider enabling them\. If no password policy is enabled, create and configure one\. See [Setting an Account Password Policy for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingPasswordPolicies.html)\. 

**Additional Resources**  
[Managing Passwords](https://docs.aws.amazon.com/IAM/latest/UserGuide/Credentials-ManagingPasswords.html)

**Report columns**  
+ Password Policy
+ Uppercase
+ Lowercase
+ Number
+ Non\-alphanumeric

## IAM Use<a name="iam-use"></a>

**Description**  
Checks for your use of IAM\. You can use IAM to create users, groups, and roles in AWS\. You can also use permissions to control access to AWS resources\. This check is intended to discourage the use of root access by checking for existence of at least one IAM user\. You can ignore the alert if you are following best practice of centralizing identities and configuring users in an [external identity provider](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html) or [AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](http://aws.amazon.com/single-sign-on/)\. 

**Check ID**  
`zXCkfM1nI3`

**Alert Criteria**  
Yellow: No IAM users have been created for this account\. 

**Recommended Action**  
Create an IAM user or use AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to create additional users whose permissions are limited to perform specific tasks in your AWS environment\. 

**Additional Resources**  
+ [What is AWS IAM Identity Center \(successor to AWS Single Sign\-On\)?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
+ [What Is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/IAM_Introduction.html)

## MFA on Root Account<a name="mfa-root-account"></a>

**Description**  
Checks the root account and warns if multi\-factor authentication \(MFA\) is not enabled\.   
For increased security, we recommend that you protect your account by using MFA, which requires a user to enter a unique authentication code from their MFA hardware or virtual device when interacting with the AWS Management Console and associated websites\.

**Check ID**  
`7DAFEmoDos`

**Alert Criteria**  
Red: MFA is not enabled on the root account\. 

**Recommended Action**  
Log in to your root account and activate an MFA device\. See [Checking MFA Status](https://docs.aws.amazon.com/IAM/latest/UserGuide/MFADeviceStatus.html) and [Setting Up an MFA Device](https://docs.aws.amazon.com/IAM/latest/UserGuide/MFADeviceSetup.html)\. 

**Additional Resources**  
[Using Multi\-Factor Authentication \(MFA\) Devices with AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingMFA.html)

## Security Groups – Specific Ports Unrestricted<a name="security-groups-specific-ports-unrestricted"></a>

**Description**  
Checks security groups for rules that allow unrestricted access \(0\.0\.0\.0/0\) to specific ports\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\. The ports with highest risk are flagged red, and those with less risk are flagged yellow\. Ports flagged green are typically used by applications that require unrestricted access, such as HTTP and SMTP\.  
If you have intentionally configured your security groups in this manner, we recommend using additional security measures to secure your infrastructure \(such as IP tables\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`HCP4007jGY`

**Alert Criteria**  
+ Green: Access to port 80, 25, 443, or 465 is unrestricted\.
+ Red: Access to port 20, 21, 1433, 1434, 3306, 3389, 4333, 5432, or 5500 is unrestricted\.
+ Yellow: Access to any other port is unrestricted\. 

**Recommended Action**  
 Restrict access to only those IP addresses that require it\. To restrict access to a specific IP address, set the suffix to /32 \(for example, 192\.0\.2\.10/32\)\. Be sure to delete overly permissive rules after creating rules that are more restrictive\.

**Additional Resources**  
+ [Amazon EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)

  [List of TCP and UDP port numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
+ [Classless Inter\-Domain Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

**Report columns**  
+ Status
+ Region
+ Security Group Name
+ Security Group ID
+ Protocol
+ From Port
+ To Port

## Security Groups – Unrestricted Access<a name="security-groups-unrestricted-access"></a>

**Description**  
Checks security groups for rules that allow unrestricted access to a resource\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`1iG5NDGVre`

**Alert Criteria**  
Red: A security group rule has a source IP address with a /0 suffix for ports other than 25, 80, or 443\. 

**Recommended Action**  
Restrict access to only those IP addresses that require it\. To restrict access to a specific IP address, set the suffix to /32 \(for example, 192\.0\.2\.10/32\)\. Be sure to delete overly permissive rules after creating rules that are more restrictive\. 

**Additional Resources**  
+ [Amazon EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)
+ [Classless Inter\-Domain Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

**Report columns**  
+ Status
+ Region
+ Security Group Name
+ Security Group ID
+ Protocol
+ From Port
+ To Port
+ IP Range