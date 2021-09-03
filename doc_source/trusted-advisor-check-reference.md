# AWS Trusted Advisor check reference<a name="trusted-advisor-check-reference"></a>

You can view all Trusted Advisor check names, descriptions, and IDs in the following reference\. You can also sign in to the [Trusted Advisor](https://console.aws.amazon.com/trustedadvisor) console to view more information about the checks, recommended actions, and their statuses\.

If you have a Business or Enterprise Support plan, you can also use the [AWS Support API](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html) and the AWS Command Line Interface \(AWS CLI\) to access your checks\. For more information, see the following topics:
+ [Using Trusted Advisor as a web service](trustedadvisor.md)
+ [Available AWS Support commands](https://docs.aws.amazon.com/cli/latest/reference/support/index.html) in the *AWS CLI Command Reference*

**Note**  
If you have a Basic Support and Developer Support plan, you can use the Trusted Advisor console to access all checks in the [Service limits](#service-limits) category and the following checks in the security category:  
[Amazon EBS Public Snapshots](#amazon-ebs-public-snapshots)
[Amazon RDS Public Snapshots](#amazon-rds-public-snapshots)
[Amazon S3 Bucket Permissions](#amazon-s3-bucket-permissions)
[IAM Use](#iam-use)
[MFA on Root Account](#mfa-root-account)
[Security Groups – Unrestricted Access](#security-groups-unrestricted-access)

**Topics**
+ [Cost optimization](#cost-optimization-checks)
+ [Performance](#performance-checks)
+ [Security](#security-checks)
+ [Fault tolerance](#fault-tolerance-checks)
+ [Service limits](#service-limits)

## Cost optimization<a name="cost-optimization-checks"></a>

You can use the following checks for the cost optimization category\.

**Contents**
+ [Amazon EC2 Reserved Instance Lease Expiration](#amazon-ec2-reserved-instances-lease-expiration)
+ [Amazon EC2 Reserved Instance Optimization](#amazon-ec2-reserved-instances-optimization)
+ [Amazon ElastiCache Reserved Node Optimization](#amazon-elasticache-reserved-node-optimization)
+ [Amazon Elasticsearch Reserved Instance Optimization](#amazon-elasticsearch-reserved-instance-optimization)
+ [Amazon RDS Idle DB Instances](#amazon-rds-idle-dbs-instances)
+ [Amazon Redshift Reserved Node Optimization](#amazon-redshift-reserved-node-optimization)
+ [Amazon Relational Database Service \(RDS\) Reserved Instance Optimization](#amazon-rds-reserved-instance-optimization)
+ [Amazon Route 53 Latency Resource Record Sets](#amazon-route-53-latency-resource-record-sets)
+ [AWS Lambda Functions with Excessive Timeouts](#aws-lambda-functions-excessive-timeouts)
+ [AWS Lambda Functions with High Error Rates](#aws-lambda-functions-with-high-error-rates)
+ [Idle Load Balancers](#idle-load-balancers)
+ [Low Utilization Amazon EC2 Instances](#low-utilization-amazon-ec2-instances)
+ [Savings Plan](#savings-plan)
+ [Unassociated Elastic IP Addresses](#unassociated-elastic-ip-addresses)
+ [Underutilized Amazon EBS Volumes](#underutilized-amazon-ebs-volumes)
+ [Underutilized Amazon Redshift Clusters](#underutilized-amazon-redshift-clusters)

### Amazon EC2 Reserved Instance Lease Expiration<a name="amazon-ec2-reserved-instances-lease-expiration"></a>

**Description**  
Checks for Amazon EC2 Reserved Instances that are scheduled to expire within the next 30 days, or have expired in the preceding 30 days\.   
Reserved Instances don't renew automatically\. You can continue using an Amazon EC2 instance covered by the reservation without interruption, but you will be charged On\-Demand rates\. New Reserved Instances can have the same parameters as the expired ones, or you can purchase Reserved Instances with different parameters\.   
The estimated monthly savings is the difference between the On\-Demand and Reserved Instance rates for the same instance type\. 

**Check ID**  
`1e93e4c0b5`

### Amazon EC2 Reserved Instance Optimization<a name="amazon-ec2-reserved-instances-optimization"></a>

**Description**  
An important part of using AWS involves balancing your Reserved Instance \(RI\) purchase against your On\-Demand Instance usage\. This check provides recommendations on which RIs will help reduce the costs incurred from using On\-Demand Instances\.   
We create these recommendations by analyzing your On\-Demand usage for the past 30 days\. We then categorizing the usage into eligible categories for reservations\. We simulate every combination of reservations in the generated category of usage to identify the recommended number of each type of RI to purchase\. This process of simulation and optimization allows us to maximize your cost savings\. This check covers recommendations based on Standard Reserved Instances with the partial upfront payment option\.  
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`cX3c2R1chu`

### Amazon ElastiCache Reserved Node Optimization<a name="amazon-elasticache-reserved-node-optimization"></a>

**Description**  
Checks your usage of ElastiCache and provides recommendations on purchase of Reserved Nodes\. These recommendations are offered to reduce the costs incurred from using ElastiCache On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Node to purchase to maximize your savings\. This check covers recommendations based on the partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`h3L1otH3re`

### Amazon Elasticsearch Reserved Instance Optimization<a name="amazon-elasticsearch-reserved-instance-optimization"></a>

**Description**  
Checks your usage of Elasticsearch and provides recommendations on purchase of Reserved Instances\. These recommendations are offered to reduce the costs incurred from using Elasticsearch On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`7ujm6yhn5t`

### Amazon RDS Idle DB Instances<a name="amazon-rds-idle-dbs-instances"></a>

**Description**  
Checks the configuration of your Amazon Relational Database Service \(Amazon RDS\) for any database \(DB\) instances that appear to be idle\.  
If a DB instance has not had a connection for a prolonged period of time, you can delete the instance to reduce costs\. If persistent storage is needed for data on the instance, you can use lower\-cost options such as taking and retaining a DB snapshot\. Manually created DB snapshots are retained until you delete them\.

**Check ID**  
`Ti39halfu8`

### Amazon Redshift Reserved Node Optimization<a name="amazon-redshift-reserved-node-optimization"></a>

**Description**  
Checks your usage of Amazon Redshift and provides recommendations on purchase of Reserved Nodes to help reduce costs incurred from using Amazon Redshift On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Nodes to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qw23er45t`

### Amazon Relational Database Service \(RDS\) Reserved Instance Optimization<a name="amazon-rds-reserved-instance-optimization"></a>

**Description**  
Checks your usage of RDS and provides recommendations on purchase of Reserved Instances to help reduce costs incurred from using RDS On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qazXsw23e`

### Amazon Route 53 Latency Resource Record Sets<a name="amazon-route-53-latency-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 latency record sets that are configured inefficiently\.   
To allow Amazon Route 53 to route queries to the AWS Region with the lowest network latency, you should create latency resource record sets for a particular domain name \(such as example\.com\) in different Regions\. If you create only one latency resource record set for a domain name, all queries are routed to one Region, and you pay extra for latency\-based routing without getting the benefits\.   
Hosted zones created by AWS services won’t appear in your check results\. 

**Check ID**  
`51fC20e7I2`

### AWS Lambda Functions with Excessive Timeouts<a name="aws-lambda-functions-excessive-timeouts"></a>

**Description**  
Checks for Lambda functions with high timeout rates that might result in high cost\.   
Lambda charges based on run time and number of requests for your function\. Function timeouts result in errors that may cause retries\. Retrying functions will incur additionally request and run time charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. 

**Check ID**  
`L4dfs2Q3C3`

### AWS Lambda Functions with High Error Rates<a name="aws-lambda-functions-with-high-error-rates"></a>

**Description**  
Checks for Lambda functions with high error rates that might result in higher costs\.   
Lambda charges are based on the number of requests and aggregate run time for your function\. Function errors may cause retries that incur additional charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. 

**Check ID**  
`L4dfs2Q3C2`

### Idle Load Balancers<a name="idle-load-balancers"></a>

**Description**  
Checks your Elastic Load Balancing configuration for load balancers that are idle\.   
Any load balancer that is configured accrues charges\. If a load balancer has no associated back\-end instances, or if network traffic is severely limited, the load balancer is not being used effectively\. This check currently only checks for Classic Load Balancer type within ELB service\. It does not include other ELB types \(Application Load Balancer, Network Load Balancer\)\.

**Check ID**  
`hjLMh88uM8`

### Low Utilization Amazon EC2 Instances<a name="low-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. This check alerts you if the daily CPU utilization was 10% or less and network I/O was 5 MB or less for at least 4 days\.  
Running instances generate hourly usage charges\. Although some scenarios can result in low utilization by design, you can often lower your costs by managing the number and size of your instances\.   
Estimated monthly savings are calculated by using the current usage rate for On\-Demand Instances and the estimated number of days the instance might be underutilized\. Actual savings will vary if you are using Reserved Instances or Spot Instances, or if the instance is not running for a full day\. To get daily utilization data, download the report for this check\. 

**Check ID**  
`Qch7DwouX1`

### Savings Plan<a name="savings-plan"></a>

**Description**  
Checks your usage of Amazon EC2, Fargate, and Lambda over the last 30 days and provides Savings Plan purchase recommendations\. These recommendations allow you to commit to a consistent usage amount measured in dollars per hour for a one\- or three\-year term in exchange for discounted rates\.   
These are sourced from AWS Cost Explorer, which can get more detailed recommendation information\. You can also purchase a savings pan through Cost Explorer\. These recommendations should be considered an alternative to your RI recommendations\. We suggest that you act on one set of recommendations only\. Acting on both sets can lead to over\-commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`vZ2c2W1srf`

### Unassociated Elastic IP Addresses<a name="unassociated-elastic-ip-addresses"></a>

**Description**  
Checks for Elastic IP addresses \(EIPs\) that are not associated with a running Amazon Elastic Compute Cloud \(Amazon EC2\) instance\.   
EIPs are static IP addresses designed for dynamic cloud computing\. Unlike traditional static IP addresses, EIPs mask the failure of an instance or Availability Zone by remapping a public IP address to another instance in your account\. A nominal charge is imposed for an EIP that is not associated with a running instance\.

**Check ID**  
`Z4AUBRNSmz`

### Underutilized Amazon EBS Volumes<a name="underutilized-amazon-ebs-volumes"></a>

**Description**  
Checks Amazon Elastic Block Store \(Amazon EBS\) volume configurations and warns when volumes appear to be underutilized\.   
Charges begin when a volume is created\. If a volume remains unattached or has very low write activity \(excluding boot volumes\) for a period of time, the volume is underutilized\. We recommend that you remove underutilized volumes to reduce costs\.

**Check ID**  
`DAvU99Dc4C`

### Underutilized Amazon Redshift Clusters<a name="underutilized-amazon-redshift-clusters"></a>

**Description**  
Checks your Amazon Redshift configuration for clusters that appear to be underutilized\.   
If an Amazon Redshift cluster has not had a connection for a prolonged period of time, or is using a low amount of CPU, you can use lower\-cost options such as downsizing the cluster, or shutting down the cluster and taking a final snapshot\. Final snapshots are retained even after you delete your cluster\.

**Check ID**  
`G31sQ1E9U`

## Performance<a name="performance-checks"></a>

Improve the performance of your service by checking your service quotas \(formerly referred to as limits\), so that you can take advantage of provisioned throughput, monitor for overutilized instances, and detect any unused resources\.

You can use the following checks for the performance category\.

**Contents**
+ [Amazon EBS Provisioned IOPS \(SSD\) Volume Attachment Configuration](#EBS-ProvisionedIOPSRule)
+ [Amazon EC2 to EBS Throughput Optimization](#ebs-throughput-optimization)
+ [Amazon Route 53 Alias Resource Record Sets](#r53-record-sets-alias)
+ [CloudFront Alternate Domain Names](#cloudfront-domain-name-check)
+ [CloudFront Content Delivery Optimization](#cloudfront-content-delivery-optimization)
+ [CloudFront Header Forwarding and Cache Hit Ratio](#cloudfront-forwarded-headers)
+ [High Utilization Amazon EC2 Instances](#high-utilization-amazon-ec2-instances)
+ [Large Number of EC2 Security Group Rules Applied to an Instance](#large-number-ec2-secuity-group-rules)
+ [Large Number of Rules in an EC2 Security Group](#large-number-rules-ec2-security-group)
+ [Overutilized Amazon EBS Magnetic Volumes](#overutilized-amazon-ebs-magnetic-volumes)

### Amazon EBS Provisioned IOPS \(SSD\) Volume Attachment Configuration<a name="EBS-ProvisionedIOPSRule"></a>

**Description**  
Checks for Provisioned IOPS \(SSD\) volumes that are attached to an Amazon EBS optimizable Amazon Elastic Compute Cloud \(Amazon EC2\) instance that is not EBS\-optimized\.   
Provisioned IOPS \(SSD\) volumes in the Amazon Elastic Block Store \(Amazon EBS\) are designed to deliver the expected performance only when they are attached to an EBS\-optimized instance\.

**Check ID**  
`PPkZrjsH2q`

### Amazon EC2 to EBS Throughput Optimization<a name="ebs-throughput-optimization"></a>

**Description**  
Checks for Amazon EBS volumes whose performance might be affected by the maximum throughput capability of the Amazon EC2 instance they are attached to\.   
To optimize performance, you should ensure that the maximum throughput of an Amazon EC2 instance is greater than the aggregate maximum throughput of the attached EBS volumes\. This check computes the total EBS volume throughput for each five\-minute period in the preceding day \(based on Coordinated Universal Time \(UTC\)\) for each EBS\-optimized instance and alerts you if usage in more than half of those periods was greater than 95% of the maximum throughput of the EC2 instance\.

**Check ID**  
`Bh2xRR2FGH`

### Amazon Route 53 Alias Resource Record Sets<a name="r53-record-sets-alias"></a>

**Description**  
Checks for resource record sets that can be changed to alias resource record sets to improve performance and save money\.   
An alias resource record set routes DNS queries to an AWS resource \(for example, an Elastic Load Balancing load balancer or an Amazon S3 bucket\) or to another Route 53 resource record set\. When you use alias resource record sets, Route 53 routes your DNS queries to AWS resources free of charge\.  
Hosted zones created by AWS services won’t appear in your check results\.

**Check ID**  
`B913Ef6fb4`

### CloudFront Alternate Domain Names<a name="cloudfront-domain-name-check"></a>

**Description**  
Checks Amazon CloudFront distributions for alternate domain names \(CNAMES\) that have incorrectly configured DNS settings\.   
If a CloudFront distribution includes alternate domain names, the DNS configuration for the domains must route DNS queries to that distribution\.  
This check assumes Amazon Route 53 DNS and Amazon CloudFront distribution are configured in the same AWS account\. As such the alert list might include resources otherwise working as expected due to DNS setting outsides of this AWS account\.

**Check ID**  
`N420c450f2`

### CloudFront Content Delivery Optimization<a name="cloudfront-content-delivery-optimization"></a>

**Description**  
Checks for cases where data transfer from Amazon Simple Storage Service \(Amazon S3\) buckets could be accelerated by using Amazon CloudFront, the AWS global content delivery service\.   
When you configure CloudFront to deliver your content, requests for your content are automatically routed to the nearest edge location where content is cached\. This routing allows content to be delivered to your users with the best possible performance\. A high ratio of data transferred out compared to the data stored in the bucket indicates that you could benefit from using Amazon CloudFront to deliver the data\.

**Check ID**  
`796d6f3D83`

### CloudFront Header Forwarding and Cache Hit Ratio<a name="cloudfront-forwarded-headers"></a>

**Description**  
Checks the HTTP request headers that CloudFront currently receives from the client and forwards to your origin server\.  
Some headers, such as date, or user\-agent, significantly reduce the cache hit ratio \(the proportion of requests that are served from a CloudFront edge cache\)\. This increases the load on your origin and reduces performance, because CloudFront must forward more requests to your origin\.

**Check ID**  
`N420c450f2`

### High Utilization Amazon EC2 Instances<a name="high-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. An alert is sent if daily CPU utilization was greater than 90% on four or more days\.  
Consistent high utilization can indicate optimized, steady performance\. However, it can also indicate that an application does not have enough resources\. To get daily CPU utilization data, download the report for this check\.

**Check ID**  
`ZRxQlPsb6c`

### Large Number of EC2 Security Group Rules Applied to an Instance<a name="large-number-ec2-secuity-group-rules"></a>

**Description**  
Checks for Amazon Elastic Compute Cloud \(Amazon EC2\) instances that have a large number of security group rules\. Performance can be degraded if an instance has a large number of rules\.

**Check ID**  
`j3DFqYTe29`

### Large Number of Rules in an EC2 Security Group<a name="large-number-rules-ec2-security-group"></a>

**Description**  
Checks each Amazon Elastic Compute Cloud \(Amazon EC2\) security group for an excessive number of rules\.   
If a security group has a large number of rules, performance can be degraded\.

**Check ID**  
`tfg86AVHAZ`

### Overutilized Amazon EBS Magnetic Volumes<a name="overutilized-amazon-ebs-magnetic-volumes"></a>

**Description**  
Checks for Amazon Elastic Block Store \(Amazon EBS\) magnetic volumes that are potentially overutilized and might benefit from a more efficient configuration\.   
A magnetic volume is designed for applications with moderate or bursty input/output \(I/O\) requirements, and the IOPS rate is not guaranteed\. It delivers approximately 100 IOPS on average, with a best\-effort ability to burst to hundreds of IOPS\. For consistently higher IOPS, you can use a Provisioned IOPS \(SSD\) volume\. For bursty IOPS, you can use a General Purpose \(SSD\) volume\. For more information, see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)\.

**Check ID**  
`k3J2hns32g`

## Security<a name="security-checks"></a>

You can use the following checks for the security category\.

**Contents**
+ [Amazon EBS Public Snapshots](#amazon-ebs-public-snapshots)
+ [Amazon RDS Public Snapshots](#amazon-rds-public-snapshots)
+ [Amazon RDS Security Group Access Risk](#amazon-rds-security-group-access-risk)
+ [Amazon Route 53 MX Resource Record Sets and Sender Policy Framework](#amazon-route-53-mx-resorc-resource-record-sets-sender-policy-framework)
+ [Amazon S3 Bucket Permissions](#amazon-s3-bucket-permissions)
+ [AWS CloudTrail Logging](#aws-cloudtrail-logging)
+ [AWS Lambda Functions Using Deprecated Runtimes](#aws-lambda-functions-deprecated-runtimes)
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

### Amazon EBS Public Snapshots<a name="amazon-ebs-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Elastic Block Store \(Amazon EBS\) volume snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`ePs02jT06w`

### Amazon RDS Public Snapshots<a name="amazon-rds-public-snapshots"></a>

**Description**  
Checks the permission settings for your Amazon Relational Database Service \(Amazon RDS\) DB snapshots and alerts you if any snapshots are marked as public\.   
When you make a snapshot public, you give all AWS accounts and users access to all the data on the snapshot\. If you want to share a snapshot only with specific users or accounts, mark the snapshot as private\. Then, specify the user or accounts you want to share the snapshot data with\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`rSs93HQwa1`

### Amazon RDS Security Group Access Risk<a name="amazon-rds-security-group-access-risk"></a>

**Description**  
Checks security group configurations for Amazon Relational Database Service \(Amazon RDS\) and warns when a security group rule grants overly permissive access to your database\. The recommended configuration for a security group rule is to allow access only from specific Amazon Elastic Compute Cloud \(Amazon EC2\) security groups or from a specific IP address\. 

**Check ID**  
`nNauJisYIT`

### Amazon Route 53 MX Resource Record Sets and Sender Policy Framework<a name="amazon-route-53-mx-resorc-resource-record-sets-sender-policy-framework"></a>

**Description**  
For each MX resource record set, checks that the TXT or SPF resource record set contains a valid SPF record\. The record must start with "`v=spf1`"\. The SPF record specifies the servers that are authorized to send email for your domain, which helps detect and stop email address spoofing and to reduce spam\. Route 53 recommends that you use a TXT record instead of an SPF record\. Trusted Advisor reports this check as green as long as each MX resource record set has at least one SPF or TXT record\.

**Check ID**  
`c9D319e7sG`

### Amazon S3 Bucket Permissions<a name="amazon-s3-bucket-permissions"></a>

**Description**  
Checks buckets in Amazon Simple Storage Service \(Amazon S3\) that have open access permissions, or that allow access to any authenticated AWS user\.   
This check examines explicit bucket permissions, as well as bucket policies that might override those permissions\. Granting list access permissions to all users for an Amazon S3 bucket is not recommended\. These permissions can lead to unintended users listing objects in the bucket at high frequency, which can result in higher than expected charges\. Permissions that grant upload and delete access to everyone can lead to security vulnerabilities in your bucket\.

**Check ID**  
`Pfx0RwqBli`

### AWS CloudTrail Logging<a name="aws-cloudtrail-logging"></a>

**Description**  
Checks your use of AWS CloudTrail\. CloudTrail provides increased visibility into activity in your AWS account by recording information about AWS API calls made on the account\. You can use these logs to determine, for example, what actions a particular user has taken during a specified time period, or which users have taken actions on a particular resource during a specified time period\.   
Because CloudTrail delivers log files to an Amazon Simple Storage Service \(Amazon S3\) bucket, CloudTrail must have write permissions for the bucket\. If a trail applies to all Regions \(the default when creating a new trail\), the trail appears multiple times in the Trusted Advisor report\.

**Check ID**  
`vjafUGJ9H0`

### AWS Lambda Functions Using Deprecated Runtimes<a name="aws-lambda-functions-deprecated-runtimes"></a>

**Description**  
Checks for Lambda functions that are configured to use a runtime that is approaching deprecation, or is deprecated\. Deprecated runtimes are not eligible for security updates or technical support\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`L4dfs2Q4C5`

### CloudFront Custom SSL Certificates in the IAM Certificate Store<a name="cloudfront-custom-ssl-certificates-iam-certificate-store"></a>

**Description**  
Checks the SSL certificates for CloudFront alternate domain names in the IAM certificate store\. This check alerts you if a certificate is expired, will expire soon, uses outdated encryption, or is not configured correctly for the distribution\.   
When a custom certificate for an alternate domain name expires, browsers that display your CloudFront content might show a warning message about the security of your website\. Certificates that are encrypted by using the SHA\-1 hashing algorithm are being deprecated by web browsers such as Chrome and Firefox\. A certificate must contain a domain name that matches either the Origin Domain Name or the domain name in the host header of a viewer request\. If it doesn't match, CloudFront returns an HTTP status code of 502 \(bad gateway\) to the user\.   
For more information, see [Using Alternate Domain Names and HTTPS](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html#CNAMEsAndHTTPS)\.

**Check ID**  
`N425c450f2`

### CloudFront SSL Certificate on the Origin Server<a name="cloudfront-ssl-certificate-origin-server"></a>

**Description**  
Checks your origin server for SSL certificates that are expired, about to expire, missing, or that use outdated encryption\. If a certificate has one of these issues, CloudFront responds to requests for your content with HTTP status code 502, Bad Gateway\.

**Check ID**  
`N430c450f2`

### ELB Listener Security<a name="elb-listener-security"></a>

**Description**  
Checks for load balancers with listeners that do not use recommended security configurations for encrypted communication\. AWS recommends using a secure protocol \(HTTPS or SSL\), up\-to\-date security policies, as well as ciphers and protocols that are secure\.  
When you use a secure protocol for a front\-end connection \(client to load balancer\), the requests are encrypted between your clients and the load balancer, which create a more secure environment\. Elastic Load Balancing provides predefined security policies with ciphers and protocols that adhere to AWS security best practices\. New versions of predefined policies are released as new configurations become available\.

**Check ID**  
`a2sEc6ILx`

### ELB Security Groups<a name="elb-security-groups"></a>

**Description**  
Checks for load balancers configured with a missing security group, or a security group that allows access to ports that are not configured for the load balancer\.   
If a security group associated with a load balancer is deleted, the load balancer will not work as expected\. If a security group allows access to ports that are not configured for the load balancer, the risk of loss of data or malicious attacks increases\.

**Check ID**  
`xSqX82fQu`

### Exposed Access Keys<a name="exposed-access-keys"></a>

**Description**  
Checks popular code repositories for access keys that have been exposed to the public and for irregular Amazon Elastic Compute Cloud \(Amazon EC2\) usage that could be the result of a compromised access key\.   
An access key consists of an access key ID and the corresponding secret access key\. Exposed access keys pose a security risk to your account and other users, could lead to excessive charges from unauthorized activity or abuse, and violate the [AWS Customer Agreement](http://aws.amazon.com/agreement)\.   
If your access key is exposed, take immediate action to secure your account\. To protect your account from excessive charges, AWS temporarily limits your ability to create some AWS resources\. This does not make your account secure\. It only partially limits the unauthorized usage for which you could be charged\.  
This check doesn't guarantee the identification of exposed access keys or compromised EC2 instances\. You are ultimately responsible for the safety and security of your access keys and AWS resources\.

**Check ID**  
`12Fnkpl8Y5`

### IAM Access Key Rotation<a name="iam-access-key-rotation"></a>

**Description**  
Checks for active IAM access keys that have not been rotated in the last 90 days\.   
When you rotate your access keys regularly, you reduce the chance that a compromised key could be used without your knowledge to access resources\. For the purposes of this check, the last rotation date and time is when the access key was created or most recently activated\. The access key number and date come from the `access_key_1_last_rotated` and `access_key_2_last_rotated` information in the most recent IAM credential report\.

**Check ID**  
`DqdJqYeRm5`

### IAM Password Policy<a name="iam-password-policy"></a>

**Description**  
Checks the password policy for your account and warns when a password policy is not enabled, or if password content requirements have not been enabled\.   
Password content requirements increase the overall security of your AWS environment by enforcing the creation of strong user passwords\. When you create or change a password policy, the change is enforced immediately for new users but does not require existing users to change their passwords\.

**Check ID**  
`Yw2K9puPzl`

### IAM Use<a name="iam-use"></a>

**Description**  
Checks for your use of IAM\. You can use IAM to create users, groups, and roles in AWS\.You can also use permissions to control access to AWS resources\. This check is intended to discourage the use of root access by checking for existence of at least one IAM user\.

**Check ID**  
`zXCkfM1nI3`

### MFA on Root Account<a name="mfa-root-account"></a>

**Description**  
Checks the root account and warns if multi\-factor authentication \(MFA\) is not enabled\.   
For increased security, we recommend that you protect your account by using MFA, which requires a user to enter a unique authentication code from their MFA hardware or virtual device when interacting with the AWS Management Console and associated websites\.

**Check ID**  
`7DAFEmoDos`

### Security Groups – Specific Ports Unrestricted<a name="security-groups-specific-ports-unrestricted"></a>

**Description**  
Checks security groups for rules that allow unrestricted access \(0\.0\.0\.0/0\) to specific ports\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\. The ports with highest risk are flagged red, and those with less risk are flagged yellow\. Ports flagged green are typically used by applications that require unrestricted access, such as HTTP and SMTP\.  
If you have intentionally configured your security groups in this manner, we recommend using additional security measures to secure your infrastructure \(such as IP tables\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`HCP4007jGY`

### Security Groups – Unrestricted Access<a name="security-groups-unrestricted-access"></a>

**Description**  
Checks security groups for rules that allow unrestricted access to a resource\.   
Unrestricted access increases opportunities for malicious activity \(hacking, denial\-of\-service attacks, loss of data\)\.  
This check only evaluates security groups that you create and their inbound rules for IPv4 addresses\. Security groups created by AWS Directory Service are flagged as red or yellow, but they don’t pose a security risk and can be safely ignored or excluded\. For more information, see the [Trusted Advisor FAQ](http://aws.amazon.com/premiumsupport/faqs/#AWS_Trusted_Advisor)\. 

**Check ID**  
`1iG5NDGVre`

## Fault tolerance<a name="fault-tolerance-checks"></a>

You can use the following checks for the fault tolerance category\.

**Contents**
+ [Amazon Aurora DB Instance Accessibility](#amazon-aurora-db-instance-accessibility)
+ [Amazon EBS Snapshots](#amazon-ebs-snapshots)
+ [Amazon EC2 Availability Zone Balance](#amazon-ecs-availability-zone-balance)
+ [Amazon RDS Backups](#amazon-rds-backups)
+ [Amazon RDS Multi\-AZ](#amazon-rds-multi-az)
+ [Amazon Route 53 Deleted Health Checks](#amazon-route-53-deleted-health-checks)
+ [Amazon Route 53 Failover Resource Record Sets](#amazon-route-53-failover-resource-record-sets)
+ [Amazon Route 53 High TTL Resource Record Sets](#amazon-route-53-high-ttl-resource-record-sets)
+ [Amazon Route 53 Name Server Delegations](#amazon-route-53-name-server-delegations)
+ [Amazon S3 Bucket Logging](#amazon-s3-bucket-logging)
+ [Amazon S3 Bucket Versioning](#amazon-s3-bucket-versioning)
+ [Auto Scaling Group Health Check](#auto-scaling-group-health-check)
+ [Auto Scaling Group Resources](#auto-scaling-group-resources)
+ [AWS Direct Connect Connection Redundancy](#aws-direct-connect-connection-redundancy)
+ [AWS Direct Connect Location Redundancy](#aws-direct-connect-location-redundancy)
+ [AWS Direct Connect Virtual Interface Redundancy](#aws-direct-connect-virtual-interface-redundancy)
+ [AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy](#aws-lambda-vpc-enabled-functions-without-multi-az-redundancy)
+ [ELB Connection Draining](#elb-connection-draining)
+ [ELB Cross\-Zone Load Balancing](#elb-cross-zone-load-balancing)
+ [Load Balancer Optimization](#load-balancer-optimization)
+ [VPN Tunnel Redundancy](#vpn-tunnel-redundancy)

### Amazon Aurora DB Instance Accessibility<a name="amazon-aurora-db-instance-accessibility"></a>

**Description**  
Checks for cases where an Amazon Aurora DB cluster has both private and public instances\.   
When your primary instance fails, a replica can be promoted to a primary instance\. If that replica is private, users who have only public access would no longer be able to connect to the database after failover\. We recommend that all the DB instances in a cluster have the same accessibility\.

**Check ID**  
`xuy7H1avtl`

### Amazon EBS Snapshots<a name="amazon-ebs-snapshots"></a>

**Description**  
Checks the age of the snapshots for your Amazon Elastic Block Store \(Amazon EBS\) volumes \(either available or in\-use\)\.   
Even though Amazon EBS volumes are replicated, failures can occur\. Snapshots are persisted to Amazon Simple Storage Service \(Amazon S3\) for durable storage and point\-in\-time recovery\.

**Check ID**  
`H7IgTzjTYb`

### Amazon EC2 Availability Zone Balance<a name="amazon-ecs-availability-zone-balance"></a>

**Description**  
Checks the distribution of Amazon Elastic Compute Cloud \(Amazon EC2\) instances across Availability Zones in a Region\.   
Availability Zones are distinct locations that are insulated from failures in other Availability Zones\. This allows inexpensive, low\-latency network connectivity between Availability Zones in the same Region\. By launching instances in multiple Availability Zones in the same Region, you can help protect your applications from a single point of failure\.

**Check ID**  
`wuy7G1zxql`

### Amazon RDS Backups<a name="amazon-rds-backups"></a>

**Description**  
Checks for automated backups of Amazon RDS DB instances\.   
By default, backups are enabled with a retention period of one day\. Backups reduce the risk of unexpected data loss and allow for point\-in\-time recovery\. 

**Check ID**  
`opQPADkZvH`

### Amazon RDS Multi\-AZ<a name="amazon-rds-multi-az"></a>

**Description**  
Checks for DB instances that are deployed in a single Availability Zone \(AZ\)\.   
Multi\-AZ deployments enhance database availability by synchronously replicating to a standby instance in a different Availability Zone\. During planned database maintenance, or the failure of a DB instance or Availability Zone, Amazon RDS automatically fails over to the standby\. This failover allows database operations to resume quickly without administrative intervention\. Because Amazon RDS does not support Multi\-AZ deployment for Microsoft SQL Server, this check does not examine SQL Server instances\.

**Check ID**  
`f2iK5R6Dep`

### Amazon Route 53 Deleted Health Checks<a name="amazon-route-53-deleted-health-checks"></a>

**Description**  
Checks for resource record sets that are associated with health checks that have been deleted\.  
Route 53 does not prevent you from deleting a health check that is associated with one or more resource record sets\. If you delete a health check without updating the associated resource record sets, the routing of DNS queries for your DNS failover configuration will not work as intended\.   
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`Cb877eB72b`

### Amazon Route 53 Failover Resource Record Sets<a name="amazon-route-53-failover-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 failover resource record sets that have a misconfiguration\.   
When Amazon Route 53 health checks determine that the primary resource is unhealthy, Amazon Route 53 responds to queries with a secondary, backup resource record set\. You must create correctly configured primary and secondary resource record sets for failover to work\.   
Hosted zones created by AWS services won't appear in your check results\. 

**Check ID**  
`b73EEdD790`

### Amazon Route 53 High TTL Resource Record Sets<a name="amazon-route-53-high-ttl-resource-record-sets"></a>

**Description**  
Checks for resource record sets that can benefit from having a lower time\-to\-live \(TTL\) value\.   
TTL is the number of seconds that a resource record set is cached by DNS resolvers\. When you specify a long TTL, DNS resolvers take longer to request updated DNS records, which can cause unnecessary delay in rerouting traffic\. For example, a long TTL creates a delay between when DNS Failover detects an endpoint failure, and when it responds by rerouting traffic\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`C056F80cR3`

### Amazon Route 53 Name Server Delegations<a name="amazon-route-53-name-server-delegations"></a>

**Description**  
Checks for Amazon Route 53 hosted zones for which your domain registrar or DNS is not using the correct Route 53 name servers\.   
When you create a hosted zone, Route 53 assigns a delegation set of four name servers\. The names of these servers are ns\-*\#\#\#*\.awsdns\-*\#\#*\.com, \.net, \.org, and \.co\.uk, where *\#\#\#* and *\#\#* typically represent different numbers\. Before Route 53 can route DNS queries for your domain, you must update your registrar's name server configuration to remove the name servers that the registrar assigned\. Then, you must add all four name servers in the Route 53 delegation set\. For maximum availability, you must add all four Route 53 name servers\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`cF171Db240`

### Amazon S3 Bucket Logging<a name="amazon-s3-bucket-logging"></a>

**Description**  
Checks the logging configuration of Amazon Simple Storage Service \(Amazon S3\) buckets\.   
When server access logging is enabled, detailed access logs are delivered hourly to a bucket that you choose\. An access log record contains details about each request, such as the request type, the resources specified in the request, and the time and date the request was processed\. By default, bucket logging is not enabled\. You should enable logging if you want to perform security audits or learn more about users and usage patterns\.  
When logging is initially enabled, the configuration is automatically validated\. However, future modifications can result in logging failures\. This check examines explicit Amazon S3 bucket permissions, but it does not examine associated bucket policies that might override the bucket permissions\.

**Check ID**  
`BueAdJ7NrP`

### Amazon S3 Bucket Versioning<a name="amazon-s3-bucket-versioning"></a>

**Description**  
Checks for Amazon Simple Storage Service buckets that do not have versioning enabled, or that have versioning suspended\.   
When versioning is enabled, you can easily recover from both unintended user actions and application failures\. Versioning allows you to preserve, retrieve, and restore any version of any object stored in a bucket\. You can use lifecycle rules to manage all versions of your objects, as well as their associated costs, by automatically archiving objects to the Glacier storage class\. Rules can also be configured to remove versions of your objects after a specified period of time\. You can also require multi\-factor authentication \(MFA\) for any object deletions or configuration changes to your buckets\.   
Versioning can't be deactivated after it has been enabled\. However, it can be suspended, which prevents new versions of objects from being created\. Using versioning can increase your costs for Amazon S3, because you pay for storage of multiple versions of an object\.

**Check ID**  
`R365s2Qddf`

### Auto Scaling Group Health Check<a name="auto-scaling-group-health-check"></a>

**Description**  
Examines the health check configuration for Auto Scaling groups\.   
If Elastic Load Balancing is being used for an Auto Scaling group, the recommended configuration is to enable an Elastic Load Balancing health check\. If an Elastic Load Balancing health check is not used, Auto Scaling can only act upon the health of the Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. Auto Scaling will not act on the application running on the instance\.

**Check ID**  
`CLOG40CDO8`

### Auto Scaling Group Resources<a name="auto-scaling-group-resources"></a>

**Description**  
Checks the availability of resources associated with launch configurations and your Auto Scaling groups\.   
Auto Scaling groups that point to unavailable resources cannot launch new Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. When properly configured, Auto Scaling causes the number of Amazon EC2 instances to increase seamlessly during demand spikes, and decrease automatically during demand lulls\. Auto Scaling groups and launch configurations that point to unavailable resources do not operate as intended\.

**Check ID**  
`8CNsSllI5v`

### AWS Direct Connect Connection Redundancy<a name="aws-direct-connect-connection-redundancy"></a>

**Description**  
Checks for AWS Regions that have only one AWS Direct Connect connection\. Connectivity to your AWS resources should have two Direct Connect connections configured at all times to provide redundancy in case a device is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`0t121N1Ty3`

### AWS Direct Connect Location Redundancy<a name="aws-direct-connect-location-redundancy"></a>

**Description**  
Checks for AWS Regions with one or more AWS Direct Connect connections and only one AWS Direct Connect location\. Connectivity to your AWS resources should have Direct Connect connections configured to different Direct Connect locations to provide redundancy in case a location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`8M012Ph3U5`

### AWS Direct Connect Virtual Interface Redundancy<a name="aws-direct-connect-virtual-interface-redundancy"></a>

**Description**  
Checks for virtual private gateways with AWS Direct Connect virtual interfaces \(VIFs\) that are not configured on at least two AWS Direct Connect connections\. Connectivity to your virtual private gateway should have multiple VIFs configured across multiple Direct Connect connections and locations\. This provides redundancy in case that a device or location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`4g3Nt5M1Th`

### AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy<a name="aws-lambda-vpc-enabled-functions-without-multi-az-redundancy"></a>

**Description**  
Checks for VPC\-enabled Lambda functions that are vulnerable to service interruption in a single Availability Zone\. It is recommended for VPC\-enabled functions to be connected to multiple Availability Zones for high availability\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`L4dfs2Q4C6`

### ELB Connection Draining<a name="elb-connection-draining"></a>

**Description**  
Checks for load balancers that do not have connection draining enabled\.   
When connection draining is not enabled and you deregister an Amazon EC2 instance from a load balancer, the load balancer stops routing traffic to that instance and closes the connection\. When connection draining is enabled, the load balancer stops sending new requests to the deregistered instance but keeps the connection open to serve active requests\.

**Check ID**  
`7qGXsKIUw`

### ELB Cross\-Zone Load Balancing<a name="elb-cross-zone-load-balancing"></a>

**Description**  
With cross\-zone load balancing turned off, there is a risk of service unavailability due to uneven distribution of traffic or backend overloading\. This problem can occur when clients incorrectly cache DNS information\. The problem can also occur when there are an unequal number of instances in each Availability Zone \(for example, if you have taken down some instances for maintenance\)\.

**Check ID**  
`xdeXZKIUy`

### Load Balancer Optimization<a name="load-balancer-optimization"></a>

**Description**  
Checks your load balancer configuration\.   
To help increase the level of fault tolerance in Amazon Elastic Compute Cloud \(Amazon EC2\) when using Elastic Load Balancing , we recommend running an equal number of instances across multiple Availability Zones in a Region\. A load balancer that is configured accrues charges, so this is a cost\-optimization check as well\.

**Check ID**  
`iqdCTZKCUp`

### VPN Tunnel Redundancy<a name="vpn-tunnel-redundancy"></a>

**Description**  
Checks the number of tunnels that are active for each of your VPNs\.  
A VPN should have two tunnels configured at all times\. This provides redundancy in case of outage or planned maintenance of the devices at the AWS endpoint\. For some hardware, only one tunnel is active at a time\. If a VPN has no active tunnels, charges for the VPN might still apply\. For more information, see [AWS Client VPN Administrator Guide](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/)\.

**Check ID**  
`S45wrEXrLz`

## Service limits<a name="service-limits"></a>

See the following checks for the service limits \(also known as quotas\) category\.

**Note**  
Values are based on a snapshot, so your current usage might differ\. Quota and usage data can take up to 24 hours to reflect any changes\. In cases where quotas have been recently increased, you might temporarily see utilization that exceeds the quota\.

**Contents**
+ [Auto Scaling Groups](#auto-scaling-groups)
+ [Auto Scaling Launch Configurations](#auto-scaling-launch-configurations)
+ [CloudFormation Stacks](#cloudformation-stacks)
+ [DynamoDB Read Capacity](#dynamo-db-read-capacity)
+ [DynamoDB Write Capacity](#dynamo-db-write-capacity)
+ [EBS Active Snapshots](#ebs-active-snapshots)
+ [EBS Cold HDD \(sc1\) Volume Storage](#ebs-cold-hdd-sc1-volume-storage)
+ [EBS General Purpose SSD \(gp2\) Volume Storage](#ebs-general-purpose-ssd-gp2-volume-storage)
+ [EBS General Purpose SSD \(gp3\) Volume Storage](#ebs-general-purpose-ssd-gp3-volume-storage)
+ [EBS Magnetic \(standard\) Volume Storage](#ebs-magnetic-standard-volume-storage)
+ [EBS Provisioned IOPS \(SSD\) Volume Aggregate IOPS](#ebs-provisioned-iops-ssd-volume-aggregate-iops)
+ [EBS Provisioned IOPS SSD \(io1\) Volume Storage](#ebs-provisioned-iops-ssd-io1-volume-storage)
+ [EBS Provisioned IOPS SSD \(io2\) Volume Storage](#ebs-provisioned-iops-ssd-io2-volume-storage)
+ [EBS Throughput Optimized HDD \(st1\) Volume Storage](#ebs-throughput-optimized-hdd-st1-volume-storage)
+ [EC2 On\-Demand Instances](#ec2-on-demand-instances)
+ [EC2 Reserved Instance Leases](#ec2-reserved-instance-leases)
+ [EC2\-Classic Elastic IP Addresses](#ec2-elastic-ip-addresses)
+ [EC2\-VPC Elastic IP Address](#ec2-vpc-elastic-ip-address)
+ [ELB Application Load Balancers](#elb-application-load-balancers)
+ [ELB Classic Load Balancers](#elb-classic-load-balancers)
+ [ELB Network Load Balancers](#elb-network-load-balancers)
+ [IAM Group](#iam-group)
+ [IAM Instance Profiles](#iam-instance-profiles)
+ [IAM Policies](#iam-policies)
+ [IAM Roles](#iam-roles)
+ [IAM Server Certificates](#iam-server-certificates)
+ [IAM Users](#iam-users)
+ [Kinesis Shards per Region](#kinesis-shards-per-region)
+ [RDS Cluster Parameter Groups](#rds-cluster-parameter-groups)
+ [RDS Cluster Roles](#rds-cluster-roles)
+ [RDS Clusters](#rds-clusters)
+ [RDS DB Instances](#rds-db-instances)
+ [RDS DB Manual Snapshots](#rds-db-manual-snapshots)
+ [RDS DB Parameter Groups](#rds-db-parameter-groups)
+ [RDS DB Security Groups](#rds-db-security-groups)
+ [RDS Event Subscriptions](#rds-event-subscriptions)
+ [RDS Max Auths per Security Group](#rds-max-auths-per-security-group)
+ [RDS Option Groups](#rds-option-groups)
+ [RDS Read Replicas per Master](#rds-read-replicas-per-master)
+ [RDS Reserved Instances](#rds-reserved-instances)
+ [RDS Subnet Groups](#rds-subnet-groups)
+ [RDS Subnets per Subnet Group](#rds-subnets-per-subnet-group)
+ [RDS Total Storage Quota](#rds-total-storage-quota)
+ [Route 53 Hosted Zones](#route-53-hosted-zones)
+ [Route 53 Max Health Checks](#route-53-max-health-checks)
+ [Route 53 Reusable Delegation Sets](#route-53-reusable-delegation-sets)
+ [Route 53 Traffic Policies](#route-53-traffic-policies)
+ [Route 53 Traffic Policy Instances](#route-53-traffic-policy-instances)
+ [SES Daily Sending Quota](#ses-daily-sending-quota)
+ [VPC](#vpc-quota-check)
+ [VPC Internet Gateways](#vpc-internet-gateways)

### Auto Scaling Groups<a name="auto-scaling-groups"></a>

**Description**  
Checks for usage that is more than 80% of the Auto Scaling Groups quota\.

**Check ID**  
`fW7HH0l7J9`

### Auto Scaling Launch Configurations<a name="auto-scaling-launch-configurations"></a>

**Description**  
Checks for usage that is more than 80% of the Auto Scaling launch configurations quota\.

**Check ID**  
`aW7HH0l7J9`

### CloudFormation Stacks<a name="cloudformation-stacks"></a>

**Description**  
Checks for usage that is more than 80% of the CloudFormation stacks quota\.

**Check ID**  
`gW7HH0l7J9`

### DynamoDB Read Capacity<a name="dynamo-db-read-capacity"></a>

**Description**  
Checks for usage that is more than 80% of the DynamoDB provisioned throughput limit for reads per AWS account\.

**Check ID**  
`6gtQddfEw6`

### DynamoDB Write Capacity<a name="dynamo-db-write-capacity"></a>

**Description**  
Checks for usage that is more than 80% of the DynamoDB provisioned throughput limit for writes per AWS account\.

**Check ID**  
`c5ftjdfkMr`

### EBS Active Snapshots<a name="ebs-active-snapshots"></a>

**Description**  
Checks for usage that is more than 80% of the EBS active snapshots quota\.

**Check ID**  
`eI7KK0l7J9`

### EBS Cold HDD \(sc1\) Volume Storage<a name="ebs-cold-hdd-sc1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Cold HDD \(sc1\) volume storage quota\.

**Check ID**  
`gH5CC0e3J9`

### EBS General Purpose SSD \(gp2\) Volume Storage<a name="ebs-general-purpose-ssd-gp2-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS General Purpose SSD \(gp2\) volume storage quota\.

**Check ID**  
`dH7RR0l6J9`

### EBS General Purpose SSD \(gp3\) Volume Storage<a name="ebs-general-purpose-ssd-gp3-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS General Purpose SSD \(gp3\) volume storage quota\.

**Check ID**  
`dH7RR0l6J3`

### EBS Magnetic \(standard\) Volume Storage<a name="ebs-magnetic-standard-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Magnetic \(standard\) volume storage quota\.

**Check ID**  
`cG7HH0l7J9`

### EBS Provisioned IOPS \(SSD\) Volume Aggregate IOPS<a name="ebs-provisioned-iops-ssd-volume-aggregate-iops"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS \(SSD\) volume aggregate IOPS quota\.

**Check ID**  
`tV7YY0l7J9`

### EBS Provisioned IOPS SSD \(io1\) Volume Storage<a name="ebs-provisioned-iops-ssd-io1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS SSD \(io1\) volume storage quota\.

**Check ID**  
`gI7MM0l7J9`

### EBS Provisioned IOPS SSD \(io2\) Volume Storage<a name="ebs-provisioned-iops-ssd-io2-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS SSD \(io2\) volume storage quota\.

**Check ID**  
`gI7MM0l7J2`

### EBS Throughput Optimized HDD \(st1\) Volume Storage<a name="ebs-throughput-optimized-hdd-st1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Throughput Optimized HDD \(st1\) volume storage quota\.

**Check ID**  
`wH7DD0l3J9`

### EC2 On\-Demand Instances<a name="ec2-on-demand-instances"></a>

**Description**  
Checks for usage that is more than 80% of the EC2 On\-Demand Instances quota\.

**Check ID**  
`0Xc6LMYG8P`

### EC2 Reserved Instance Leases<a name="ec2-reserved-instance-leases"></a>

**Description**  
Checks for usage that is more than 80% of the EC2 Reserved Instance leases quota\.

**Check ID**  
`iH7PP0l7J9`

### EC2\-Classic Elastic IP Addresses<a name="ec2-elastic-ip-addresses"></a>

**Description**  
Checks for usage that is more than 80% of the EC2\-Classic Elastic IP addresses quota\.

**Check ID**  
`aW9HH0l8J6`

### EC2\-VPC Elastic IP Address<a name="ec2-vpc-elastic-ip-address"></a>

**Description**  
Checks for usage that is more than 80% of the EC2\-VPC Elastic IP address quota\.

**Check ID**  
`lN7RR0l7J9`

### ELB Application Load Balancers<a name="elb-application-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Application Load Balancers quota\.

**Check ID**  
`EM8b3yLRTr`

### ELB Classic Load Balancers<a name="elb-classic-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Classic Load Balancers quota\.

**Check ID**  
`iK7OO0l7J9`

### ELB Network Load Balancers<a name="elb-network-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Network Load Balancers quota\.

**Check ID**  
`8wIqYSt25K`

### IAM Group<a name="iam-group"></a>

**Description**  
Checks for usage that is more than 80% of the IAM group quota\.

**Check ID**  
`sU7XX0l7J9`

### IAM Instance Profiles<a name="iam-instance-profiles"></a>

**Description**  
Checks for usage that is more than 80% of the IAM instance profiles quota\.

**Check ID**  
`nO7SS0l7J9`

### IAM Policies<a name="iam-policies"></a>

**Description**  
Checks for usage that is more than 80% of the IAM policies quota\.

**Check ID**  
`pR7UU0l7J9`

### IAM Roles<a name="iam-roles"></a>

**Description**  
Checks for usage that is more than 80% of the IAM roles quota\.

**Check ID**  
`oQ7TT0l7J9`

### IAM Server Certificates<a name="iam-server-certificates"></a>

**Description**  
Checks for usage that is more than 80% of the IAM server certificates quota\.

**Check ID**  
`rT7WW0l7J9`

### IAM Users<a name="iam-users"></a>

**Description**  
Checks for usage that is more than 80% of the IAM users quota\.

**Check ID**  
`qS7VV0l7J9`

### Kinesis Shards per Region<a name="kinesis-shards-per-region"></a>

**Description**  
Checks for usage that is more than 80% of the Kinesis shards per Region quota\.

**Check ID**  
`bW7HH0l7J9`

### RDS Cluster Parameter Groups<a name="rds-cluster-parameter-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS cluster parameter groups quota\.

**Check ID**  
`jtlIMO3qZM`

### RDS Cluster Roles<a name="rds-cluster-roles"></a>

**Description**  
Checks for usage that is more than 80% of the RDS cluster roles quota\.

**Check ID**  
`7fuccf1Mx7`

### RDS Clusters<a name="rds-clusters"></a>

**Description**  
Checks for usage that is more than 80% of the RDS clusters quota\.

**Check ID**  
`gjqMBn6pjz`

### RDS DB Instances<a name="rds-db-instances"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB instances quota\.

**Check ID**  
`XG0aXHpIEt`

### RDS DB Manual Snapshots<a name="rds-db-manual-snapshots"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB manual snapshots quota\.

**Check ID**  
`dV84wpqRUs`

### RDS DB Parameter Groups<a name="rds-db-parameter-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB parameter groups quota\.

**Check ID**  
`jEECYg2YVU`

### RDS DB Security Groups<a name="rds-db-security-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB security groups quota\.

**Check ID**  
`gfZAn3W7wl`

### RDS Event Subscriptions<a name="rds-event-subscriptions"></a>

**Description**  
Checks for usage that is more than 80% of the RDS event subscriptions quota\.

**Check ID**  
`keAhfbH5yb`

### RDS Max Auths per Security Group<a name="rds-max-auths-per-security-group"></a>

**Description**  
Checks for usage that is more than 80% of the RDS max auths per security group quota\.

**Check ID**  
`dBkuNCvqn5`

### RDS Option Groups<a name="rds-option-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS option groups quota\.

**Check ID**  
`3Njm0DJQO9`

### RDS Read Replicas per Master<a name="rds-read-replicas-per-master"></a>

**Description**  
Checks for usage that is more than 80% of the RDS read replicas per master quota\.

**Check ID**  
`pYW8UkYz2w`

### RDS Reserved Instances<a name="rds-reserved-instances"></a>

**Description**  
Checks for usage that is more than 80% of the RDS Reserved Instances quota\.

**Check ID**  
`UUDvOa5r34`

### RDS Subnet Groups<a name="rds-subnet-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS subnet groups quota\.

**Check ID**  
`dYWBaXaaMM`

### RDS Subnets per Subnet Group<a name="rds-subnets-per-subnet-group"></a>

**Description**  
Checks for usage that is more than 80% of the RDS subnets per subnet group quota\.

**Check ID**  
`jEhCtdJKOY`

### RDS Total Storage Quota<a name="rds-total-storage-quota"></a>

**Description**  
Checks for usage that is more than 80% of the RDS total storage quota\.

**Check ID**  
`P1jhKWEmLa`

### Route 53 Hosted Zones<a name="route-53-hosted-zones"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 hosted zones quota per account\.

**Check ID**  
`dx3xfcdfMr`

### Route 53 Max Health Checks<a name="route-53-max-health-checks"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 health checks quota per account\.

**Check ID**  
`ru4xfcdfMr`

### Route 53 Reusable Delegation Sets<a name="route-53-reusable-delegation-sets"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 reusable delegation sets quota per account\.

**Check ID**  
`ty3xfcdfMr`

### Route 53 Traffic Policies<a name="route-53-traffic-policies"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 traffic policies quota per account\.

**Check ID**  
`dx3xfbjfMr`

### Route 53 Traffic Policy Instances<a name="route-53-traffic-policy-instances"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 traffic policy instances quota per account\.

**Check ID**  
`dx8afcdfMr`

### SES Daily Sending Quota<a name="ses-daily-sending-quota"></a>

**Description**  
Checks for usage that is more than 80% of the Amazon SES daily sending quota\.

**Check ID**  
`hJ7NN0l7J9`

### VPC<a name="vpc-quota-check"></a>

**Description**  
Checks for usage that is more than 80% of the VPC quota\.

**Check ID**  
`jL7PP0l7J9`

### VPC Internet Gateways<a name="vpc-internet-gateways"></a>

**Description**  
Checks for usage that is more than 80% of the VPC Internet gateways quota\.

**Check ID**  
`kM7QQ0l7J9`