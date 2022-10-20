# Performance<a name="performance-checks"></a>

Improve the performance of your service by checking your service quotas \(formerly referred to as limits\), so that you can take advantage of provisioned throughput, monitor for overutilized instances, and detect any unused resources\.

You can use the following checks for the performance category\.

**Contents**
+ [Amazon EBS Provisioned IOPS \(SSD\) Volume Attachment Configuration](#EBS-ProvisionedIOPSRule)
+ [Amazon EBS under\-provisioned volumes](#amazon-ebs-under-provisioned-volumes)
+ [Amazon EC2 to EBS Throughput Optimization](#ebs-throughput-optimization)
+ [Amazon Route 53 Alias Resource Record Sets](#r53-record-sets-alias)
+ [AWS Lambda under\-provisioned functions for memory size](#aws-lambda-under-provisioned-functions-memory-size)
+ [AWS Well\-Architected high risk issues for performance](#well-architected-high-risk-issues-performance)
+ [CloudFront Alternate Domain Names](#cloudfront-domain-name-check)
+ [CloudFront Content Delivery Optimization](#cloudfront-content-delivery-optimization)
+ [CloudFront Header Forwarding and Cache Hit Ratio](#cloudfront-forwarded-headers)
+ [High Utilization Amazon EC2 Instances](#high-utilization-amazon-ec2-instances)
+ [Large Number of EC2 Security Group Rules Applied to an Instance](#large-number-ec2-secuity-group-rules)
+ [Large Number of Rules in an EC2 Security Group](#large-number-rules-ec2-security-group)
+ [Overutilized Amazon EBS Magnetic Volumes](#overutilized-amazon-ebs-magnetic-volumes)

## Amazon EBS Provisioned IOPS \(SSD\) Volume Attachment Configuration<a name="EBS-ProvisionedIOPSRule"></a>

**Description**  
Checks for Provisioned IOPS \(SSD\) volumes that are attached to an Amazon EBS optimizable Amazon Elastic Compute Cloud \(Amazon EC2\) instance that is not EBS\-optimized\.   
Provisioned IOPS \(SSD\) volumes in the Amazon Elastic Block Store \(Amazon EBS\) are designed to deliver the expected performance only when they are attached to an EBS\-optimized instance\.

**Check ID**  
`PPkZrjsH2q`

**Alert Criteria**  
Yellow: An Amazon EC2 instance that can be EBS\-optimized has an attached Provisioned IOPS \(SSD\) volume but the instance is not EBS\-optimized\.

**Recommended Action**  
Create a new instance that is EBS\-optimized, detach the volume, and reattach the volume to your new instance\. For more information, see [Amazon EBS\-Optimized Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html) and [Attaching an Amazon EBS Volume to an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-attaching-volume.html)\.

**Additional Resources**  
+ [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)
+ [Amazon EBS Volume Performance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html)

**Report columns**  
+ Status
+ Region/AZ
+ Volume ID
+ Volume Name
+ Volume Attachment
+ Instance ID
+ Instance Type
+ EBS Optimized

## Amazon EBS under\-provisioned volumes<a name="amazon-ebs-under-provisioned-volumes"></a>

**Description**  
Checks the Amazon Elastic Block Store \(Amazon EBS\) volumes that were running at any time during the lookback period\. This check alerts you if any EBS volumes were under\-provisioned for your workloads\. Consistent high utilization can indicate optimized, steady performance, but can also indicate that an application does not have enough resources\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM04`

**Alert Criteria**  
 Yellow: An EBS Volume that was under\-provisioned during the lookback period\. To determine if a volume is under\-provisioned, we consider all default CloudWatch metrics \(including IOPS and throughput\)\. The algorithm used to identify under\-provisioned EBS volumes follows AWS best practices\. The algorithm is updated when a new pattern has been identified\.

**Recommended Action**  
Consider upsizing volumes that have high utilization\.  
For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

**Report columns**  
+ Status
+ Region
+ Volume ID
+ Volume Type
+ Volume Size \(GB\)
+ Volume Baseline IOPS
+ Volume Burst IOPS
+ Volume Burst Throughput
+ Recommended Volume Type
+ Recommended Volume Size \(GB\)
+ Recommended Volume Baseline IOPS
+ Recommended Volume Burst IOPS
+ Recommended Volume Baseline Throughput
+ Recommended Volume Burst Throughput
+ Lookback Period \(days\)
+ Performance Risk
+ Last Updated Time

## Amazon EC2 to EBS Throughput Optimization<a name="ebs-throughput-optimization"></a>

**Description**  
Checks for Amazon EBS volumes whose performance might be affected by the maximum throughput capability of the Amazon EC2 instance they are attached to\.   
To optimize performance, you should ensure that the maximum throughput of an Amazon EC2 instance is greater than the aggregate maximum throughput of the attached EBS volumes\. This check computes the total EBS volume throughput for each five\-minute period in the preceding day \(based on Coordinated Universal Time \(UTC\)\) for each EBS\-optimized instance and alerts you if usage in more than half of those periods was greater than 95% of the maximum throughput of the EC2 instance\.

**Check ID**  
`Bh2xRR2FGH`

**Alert Criteria**  
Yellow: In the preceding day \(UTC\), the aggregate throughput \(megabytes/sec\) of the EBS volumes attached to the EC2 instance exceeded 95% of the published throughput between the instance and the EBS volumes more than 50% of time\.

**Recommended Action**  
Compare the maximum throughput of your Amazon EBS volumes \(see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)\) with the maximum throughput of the Amazon EC2 instance they are attached to\. See [Instance Types That Support EBS Optimization](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html#ebs-optimization-support)\.   
Consider attaching your volumes to an instance that supports higher throughput to Amazon EBS for optimal performance\.

**Additional Resources**  
+ [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)
+ [Amazon EBS\-Optimized Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html)
+ [Monitoring the Status of Your Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring-volume-status.html)
+ [Attaching an Amazon EBS Volume to an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-attaching-volume.html)
+ [Detaching an Amazon EBS Volume from an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-detaching-volume.html)
+ [Deleting an Amazon EBS Volume](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-deleting-volume.html)

**Report columns**  
+ Status
+ Region
+ Instance ID
+ Instance Type
+ Time Near Maximum

## Amazon Route 53 Alias Resource Record Sets<a name="r53-record-sets-alias"></a>

**Description**  
Checks for resource record sets that can be changed to alias resource record sets to improve performance and save money\.   
An alias resource record set routes DNS queries to an AWS resource \(for example, an Elastic Load Balancing load balancer or an Amazon S3 bucket\) or to another Route 53 resource record set\. When you use alias resource record sets, Route 53 routes your DNS queries to AWS resources free of charge\.  
Hosted zones created by AWS services won’t appear in your check results\.

**Check ID**  
`B913Ef6fb4`

**Alert Criteria**  
+ Yellow: A resource record set is a CNAME to an Amazon S3 website\.
+ Yellow: A resource record set is a CNAME to an Amazon CloudFront distribution\.
+ Yellow: A resource record set is a CNAME to an Elastic Load Balancing load balancer\.

**Recommended Action**  
Replace the listed CNAME resource record sets with alias resource record sets; see [Choosing Between Alias and Non\-Alias Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/CreatingAliasRRSets.html)\.   
You also need to change the record type from CNAME to A or AAAA, depending on the AWS resource\. See [Values that You Specify When You Create or Edit Amazon Route 53 Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-values.html)\.

**Additional Resources**  
[Routing Queries to AWS Resources](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-aws-resources.html)

**Report columns**  
+ Status
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Resource Record Set Type
+ Resource Record Set Identifier
+ Alias Target

## AWS Lambda under\-provisioned functions for memory size<a name="aws-lambda-under-provisioned-functions-memory-size"></a>

**Description**  
Checks the AWS Lambda functions that were invoked at least once during the lookback period\. This check alerts you if any of your Lambda functions were under\-provisioned for memory size\. When you have Lambda functions that are under\-provisioned for memory size, these functions take longer time to complete\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM06`

**Alert Criteria**  
 Yellow: A Lambda function that was under\-provisioned for memory size during the lookback period\. To determine if a Lambda function is under\-provisioned, we consider all default CloudWatch metrics for that function\. The algorithm used to identify under\-provisioned Lambda functions for memory size follows AWS best practices\. The algorithm is updated when a new pattern has been identified\.

**Recommended Action**  
 Consider increasing the memory size of your Lambda functions\.  
For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

**Report columns**  
+ Status
+ Region
+ Function Name
+ Function Version
+ Memory Size \(MB\)
+ Recommended Memory Size \(MB\)
+ Lookback Period \(days\)
+ Performance Risk
+ Last Updated Time

## AWS Well\-Architected high risk issues for performance<a name="well-architected-high-risk-issues-performance"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the performance pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L2`

**Alert Criteria**  
+ Red: At least one active high risk issue was identified in the performance pillar for AWS Well\-Architected\.
+ Green: No active high risk issues were detected in the performance pillar for AWS Well\-Architected\.

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
+ Number of identified HRIs for Performance
+ Number of HRIs resolved for Performance
+ Number of questions answered for Performance
+ Total number of questions in Performance pillar
+ Last Updated Time

## CloudFront Alternate Domain Names<a name="cloudfront-domain-name-check"></a>

**Description**  
Checks Amazon CloudFront distributions for alternate domain names \(CNAMES\) that have incorrectly configured DNS settings\.   
If a CloudFront distribution includes alternate domain names, the DNS configuration for the domains must route DNS queries to that distribution\.  
This check assumes Amazon Route 53 DNS and Amazon CloudFront distribution are configured in the same AWS account\. As such the alert list might include resources otherwise working as expected due to DNS setting outsides of this AWS account\.

**Check ID**  
`N420c450f2`

**Alert Criteria**  
+ Yellow: A CloudFront distribution includes alternate domain names, but the DNS configuration is not correctly set up with a CNAME record or an Amazon Route 53 alias resource record\.
+ Yellow: A CloudFront distribution includes alternate domain names, but Trusted Advisor could not evaluate the DNS configuration because there were too many redirects\.
+ Yellow: A CloudFront distribution includes alternate domain names, but Trusted Advisor could not evaluate the DNS configuration for some other reason, most likely because of a timeout\. 

**Recommended Action**  
 Update the DNS configuration to route DNS queries to the CloudFront distribution; see [Using Alternate Domain Names \(CNAMEs\)](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/CNAMEs.html)\.   
If you're using Amazon Route 53 as your DNS service, see [Routing Traffic to an Amazon CloudFront Web Distribution by Using Your Domain Name](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-cloudfront-distribution.html)\. If the check timed out, try refreshing the check\.

**Additional Resources**  
[Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/)

**Report columns**  
+ Status
+ Distribution ID
+ Distribution Domain Name
+ Alternate Domain Name
+ Reason

## CloudFront Content Delivery Optimization<a name="cloudfront-content-delivery-optimization"></a>

**Description**  
Checks for cases where data transfer from Amazon Simple Storage Service \(Amazon S3\) buckets could be accelerated by using Amazon CloudFront, the AWS global content delivery service\.   
When you configure CloudFront to deliver your content, requests for your content are automatically routed to the nearest edge location where content is cached\. This routing allows content to be delivered to your users with the best possible performance\. A high ratio of data transferred out compared to the data stored in the bucket indicates that you could benefit from using Amazon CloudFront to deliver the data\.

**Check ID**  
`796d6f3D83`

**Alert Criteria**  
+ Yellow: The amount of data transferred out of the bucket to your users by GET requests in the 30 days preceding the check is at least 25 times greater than the average amount of data stored in the bucket\.
+ Red: The amount of data transferred out of the bucket to your users by GET requests in the 30 days preceding the check is at least 10 TB and at least 25 times greater than the average amount of data stored in the bucket\. 

**Recommended Action**  
Consider using CloudFront for better performance\. See [Amazon CloudFront Product Details](http://aws.amazon.com/cloudfront/details)\.  
If the data transferred is 10 TB per month or more, see [Amazon CloudFront Pricing](http://aws.amazon.com/cloudfront/pricing) to explore possible cost savings\. 

**Additional Resources**  
+ [Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/)
+ [AWS Case Study: PBS](http://aws.amazon.com/solutions/case-studies/pbs/)

**Report columns**  
+ Status
+ Region
+ Bucket Name
+ S3 Storage \(GB\)
+ Data Transfer Out \(GB\)
+ Ratio of Transfer to Storage

## CloudFront Header Forwarding and Cache Hit Ratio<a name="cloudfront-forwarded-headers"></a>

**Description**  
Checks the HTTP request headers that CloudFront currently receives from the client and forwards to your origin server\.  
Some headers, such as date, or user\-agent, significantly reduce the cache hit ratio \(the proportion of requests that are served from a CloudFront edge cache\)\. This increases the load on your origin and reduces performance, because CloudFront must forward more requests to your origin\.

**Check ID**  
`N415c450f2`

**Alert Criteria**  
Yellow: One or more request headers that CloudFront forwards to your origin might significantly reduce your cache hit ratio\.

**Recommended Action**  
Consider whether the request headers provide enough benefit to justify the negative effect on the cache hit ratio\. If your origin returns the same object regardless of the value of a given header, we recommend that you don't configure CloudFront to forward that header to the origin\. For more information, see [Configuring CloudFront to Cache Objects Based on Request Headers](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/header-caching.html)\.

**Additional Resources**  
+ [Increasing the Proportion of Requests that Are Served from CloudFront Edge Caches](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cache-hit-ratio.html#cache-hit-ratio-request-headers)
+ [CloudFront Cache Statistics Reports](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cache-statistics.html)
+ [HTTP Request Headers and CloudFront Behavior](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/RequestAndResponseBehaviorCustomOrigin.html#request-custom-headers-behavior)

**Report columns**  
+ Distribution ID
+ Distribution Domain Name
+ Cache Behavior Path Pattern
+ Headers

## High Utilization Amazon EC2 Instances<a name="high-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. An alert is sent if daily CPU utilization was greater than 90% on four or more days\.  
Consistent high utilization can indicate optimized, steady performance\. However, it can also indicate that an application does not have enough resources\. To get daily CPU utilization data, download the report for this check\.

**Check ID**  
`ZRxQlPsb6c`

**Alert Criteria**  
Yellow: An instance had more than 90% daily average CPU utilization on at least 4 of the previous 14 days\. 

**Recommended Action**  
Consider adding more instances\. For information about scaling the number of instances based on demand, see [What is Auto Scaling?](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/WhatIsAutoScaling.html)

**Additional Resources**  
+ [Monitoring Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-monitoring.html)
+ [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AESDG-chapter-instancedata.html)
+ [Amazon CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/)
+ [Amazon EC2 Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/latest/userguide/)

**Report columns**  
+ Region/AZ
+ Instance ID
+ Instance Type
+ Instance Name
+ 14\-Day Average CPU Utilization
+ Number of Days over 90% CPU Utilization

## Large Number of EC2 Security Group Rules Applied to an Instance<a name="large-number-ec2-secuity-group-rules"></a>

**Description**  
Checks for Amazon Elastic Compute Cloud \(Amazon EC2\) instances that have a large number of security group rules\. Performance can be degraded if an instance has a large number of rules\.

**Check ID**  
`j3DFqYTe29`

**Alert Criteria**  
+ Yellow: An Amazon EC2\-VPC instance has more than 50 security group rules\.
+ Yellow: An Amazon EC2\-Classic instance has more than 100 security group rules\.

**Recommended Action**  
Reduce the number of rules associated with an instance by deleting unnecessary or overlapping rules\. For more information, see [Deleting Rules from a Security Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#deleting-security-group-rule)\.

**Additional Resources**  
[Amazon EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#concepts-security)

**Report columns**  
+ Region
+ Instance ID
+ Instance Name
+ VPC ID
+ Total Inbound Rules
+ Total Outbound Rules

## Large Number of Rules in an EC2 Security Group<a name="large-number-rules-ec2-security-group"></a>

**Description**  
Checks each Amazon Elastic Compute Cloud \(Amazon EC2\) security group for an excessive number of rules\.  
If a security group has a large number of rules, performance can be degraded\.

**Check ID**  
`tfg86AVHAZ`

**Alert Criteria**  
+ Yellow: An Amazon EC2\-VPC security group has more than 50 rules\.
+ Yellow: An Amazon EC2\-Classic security group has more than 100 rules\. 

**Recommended Action**  
Reduce the number of rules in a security group by deleting unnecessary or overlapping rules\. For more information, see [Deleting Rules from a Security Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#deleting-security-group-rule)\. 

**Additional Resources**  
[Amazon EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)

**Report columns**  
+ Region
+ Security Group Name
+ Group ID
+ Description
+ Instance Count
+ VPC ID
+ Total Inbound Rules
+ Total Outbound Rules

## Overutilized Amazon EBS Magnetic Volumes<a name="overutilized-amazon-ebs-magnetic-volumes"></a>

**Description**  
Checks for Amazon Elastic Block Store \(Amazon EBS\) magnetic volumes that are potentially overutilized and might benefit from a more efficient configuration\.   
A magnetic volume is designed for applications with moderate or bursty input/output \(I/O\) requirements, and the IOPS rate is not guaranteed\. It delivers approximately 100 IOPS on average, with a best\-effort ability to burst to hundreds of IOPS\. For consistently higher IOPS, you can use a Provisioned IOPS \(SSD\) volume\. For bursty IOPS, you can use a General Purpose \(SSD\) volume\. For more information, see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)\.  
 For a list of instance types that support EBS\-optimized behavior, see [Amazon EBS\-Optimized Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html)\.   
 To get daily utilization metrics, download the report for this check\. The detailed report shows a column for each of the last 14 days\. If there is no active EBS volume, the cell is empty\. If there is insufficient data to make a reliable measurement, the cell contains `N/A`\. If there is sufficient data, the cell contains the daily median and the percentage of the variance in relation to the median \(for example, `256 / 20%`\)\.

**Check ID**  
`k3J2hns32g`

**Alert Criteria**  
Yellow: An Amazon EBS Magnetic volume is attached to an instance that can be EBS\-optimized or is part of a cluster compute network with a daily median of more than 95 IOPS, and varies by less than 10% of the median value for at least 7 of the past 14 days\.

**Recommended Action**  
For consistently higher IOPS, you can use a Provisioned IOPS \(SSD\) volume\. For bursty IOPS, you can use a General Purpose \(SSD\) volume\. For more information, see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)\.

**Additional Resources**  
[Amazon Elastic Block Store \(Amazon EBS\)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)

**Report columns**  
+ Status
+ Region
+ Volume ID
+ Volume Name
+ Number of Days Over
+ Max Daily Median

**Note**  
If you opted in your account for AWS Compute Optimizer, we recommend that you use the Amazon EBS under\-provisioned volumes check instead\. For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.