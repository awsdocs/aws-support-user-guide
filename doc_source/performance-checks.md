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

## Amazon EBS under\-provisioned volumes<a name="amazon-ebs-under-provisioned-volumes"></a>

**Description**  
Checks the Amazon Elastic Block Store \(Amazon EBS\) volumes that were running at any time during the lookback period\. This check alerts you if any EBS volumes were under\-provisioned for your workloads\. Consistent high utilization can indicate optimized, steady performance, but can also indicate that an application does not have enough resources\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM04`

## Amazon EC2 to EBS Throughput Optimization<a name="ebs-throughput-optimization"></a>

**Description**  
Checks for Amazon EBS volumes whose performance might be affected by the maximum throughput capability of the Amazon EC2 instance they are attached to\.   
To optimize performance, you should ensure that the maximum throughput of an Amazon EC2 instance is greater than the aggregate maximum throughput of the attached EBS volumes\. This check computes the total EBS volume throughput for each five\-minute period in the preceding day \(based on Coordinated Universal Time \(UTC\)\) for each EBS\-optimized instance and alerts you if usage in more than half of those periods was greater than 95% of the maximum throughput of the EC2 instance\.

**Check ID**  
`Bh2xRR2FGH`

## Amazon Route 53 Alias Resource Record Sets<a name="r53-record-sets-alias"></a>

**Description**  
Checks for resource record sets that can be changed to alias resource record sets to improve performance and save money\.   
An alias resource record set routes DNS queries to an AWS resource \(for example, an Elastic Load Balancing load balancer or an Amazon S3 bucket\) or to another Route 53 resource record set\. When you use alias resource record sets, Route 53 routes your DNS queries to AWS resources free of charge\.  
Hosted zones created by AWS services won’t appear in your check results\.

**Check ID**  
`B913Ef6fb4`

## AWS Lambda under\-provisioned functions for memory size<a name="aws-lambda-under-provisioned-functions-memory-size"></a>

**Description**  
Checks the AWS Lambda functions that were invoked at least once during the lookback period\. This check alerts you if any of your Lambda functions were under\-provisioned for memory size\. When you have Lambda functions that are under\-provisioned for memory size, these functions take longer time to complete\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM06`

## AWS Well\-Architected high risk issues for performance<a name="well-architected-high-risk-issues-performance"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the performance pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L2`

## CloudFront Alternate Domain Names<a name="cloudfront-domain-name-check"></a>

**Description**  
Checks Amazon CloudFront distributions for alternate domain names \(CNAMES\) that have incorrectly configured DNS settings\.   
If a CloudFront distribution includes alternate domain names, the DNS configuration for the domains must route DNS queries to that distribution\.  
This check assumes Amazon Route 53 DNS and Amazon CloudFront distribution are configured in the same AWS account\. As such the alert list might include resources otherwise working as expected due to DNS setting outsides of this AWS account\.

**Check ID**  
`N420c450f2`

## CloudFront Content Delivery Optimization<a name="cloudfront-content-delivery-optimization"></a>

**Description**  
Checks for cases where data transfer from Amazon Simple Storage Service \(Amazon S3\) buckets could be accelerated by using Amazon CloudFront, the AWS global content delivery service\.   
When you configure CloudFront to deliver your content, requests for your content are automatically routed to the nearest edge location where content is cached\. This routing allows content to be delivered to your users with the best possible performance\. A high ratio of data transferred out compared to the data stored in the bucket indicates that you could benefit from using Amazon CloudFront to deliver the data\.

**Check ID**  
`796d6f3D83`

## CloudFront Header Forwarding and Cache Hit Ratio<a name="cloudfront-forwarded-headers"></a>

**Description**  
Checks the HTTP request headers that CloudFront currently receives from the client and forwards to your origin server\.  
Some headers, such as date, or user\-agent, significantly reduce the cache hit ratio \(the proportion of requests that are served from a CloudFront edge cache\)\. This increases the load on your origin and reduces performance, because CloudFront must forward more requests to your origin\.

**Check ID**  
`N420c450f2`

## High Utilization Amazon EC2 Instances<a name="high-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. An alert is sent if daily CPU utilization was greater than 90% on four or more days\.  
Consistent high utilization can indicate optimized, steady performance\. However, it can also indicate that an application does not have enough resources\. To get daily CPU utilization data, download the report for this check\.

**Check ID**  
`ZRxQlPsb6c`

## Large Number of EC2 Security Group Rules Applied to an Instance<a name="large-number-ec2-secuity-group-rules"></a>

**Description**  
Checks for Amazon Elastic Compute Cloud \(Amazon EC2\) instances that have a large number of security group rules\. Performance can be degraded if an instance has a large number of rules\.

**Check ID**  
`j3DFqYTe29`

## Large Number of Rules in an EC2 Security Group<a name="large-number-rules-ec2-security-group"></a>

**Description**  
Checks each Amazon Elastic Compute Cloud \(Amazon EC2\) security group for an excessive number of rules\.   
If a security group has a large number of rules, performance can be degraded\.

**Check ID**  
`tfg86AVHAZ`

## Overutilized Amazon EBS Magnetic Volumes<a name="overutilized-amazon-ebs-magnetic-volumes"></a>

**Description**  
Checks for Amazon Elastic Block Store \(Amazon EBS\) magnetic volumes that are potentially overutilized and might benefit from a more efficient configuration\.   
A magnetic volume is designed for applications with moderate or bursty input/output \(I/O\) requirements, and the IOPS rate is not guaranteed\. It delivers approximately 100 IOPS on average, with a best\-effort ability to burst to hundreds of IOPS\. For consistently higher IOPS, you can use a Provisioned IOPS \(SSD\) volume\. For bursty IOPS, you can use a General Purpose \(SSD\) volume\. For more information, see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)\.

**Check ID**  
`k3J2hns32g`

**Note**  
If you opted in your account for AWS Compute Optimizer, we recommend that you use the Amazon EBS under\-provisioned volumes check instead\. For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.