# Change log for AWS Trusted Advisor checks<a name="aws-trusted-advisor-change-log"></a>

See the following topic for recent changes to Trusted Advisor checks\. 

**Note**  
If you use the Trusted Advisor console or the AWS Support API, checks that were removed won't appear in check results\. If you use any of the removed checks such as specifying the check ID in an AWS Support API operation or your code, you must remove these checks to avoid API call errors\.

For more information about the available checks, see the [AWS Trusted Advisor check reference](trusted-advisor-check-reference.md)\.

## Added checks from AWS Compute Optimizer<a name="added-checks-compute-optimizer"></a>

Trusted Advisor added the following checks on May 4, 2022\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  Amazon EBS over\-provisioned volumes  |  Cost optimization  |  `COr6dfpM03`  | 
|  Amazon EBS under\-provisioned volumes  |  Performance  |  `COr6dfpM04`  | 
|  AWS Lambda over\-provisioned functions for memory size  |  Cost optimization  |  `COr6dfpM05`  | 
|  AWS Lambda under\-provisioned functions for memory size  |  Performance  |  `COr6dfpM06`  | 

You must opt in your AWS account for Compute Optimizer so that these checks can receive data from your Lambda and Amazon EBS resources\. For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

## Updates to the Exposed Access Keys check<a name="update-exposed-access-keys-check"></a>

Trusted Advisor updated the following check on April 25, 2022\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  Exposed Access Keys  |  Security  |  `12Fnkpl8Y5`  | 

Trusted Advisor now refreshes this check for you automatically\. This check can't be refreshed manually from the Trusted Advisor console or the AWS Support API\. If your application or code refreshes this check for your AWS account, we recommend that you update it to no longer refresh this check\. Otherwise, you will receive the `InvalidParameterValue` error\.

Any access keys that you excluded before this update will no longer be excluded and will appear as affected resources\. You can't exclude access keys from your check results\. For more information, see [Exposed Access Keys](security-checks.md#exposed-access-keys)\.

**Note**  
If you created your AWS account after April 25, 2022, the check results for Exposed Access Keys initially shows the gray icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/gray.png)\) even for unexposed access keys\. This means that Trusted Advisor hasn't identified any changes to the check\.  
If Trusted Advisor identifies a resource at risk, the status changes to the action recommended icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/red.png)\)\. After you fix or delete the resource, the check result shows the check mark icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/green.png)\)\.

## Updated checks for AWS Direct Connect<a name="updated-checks-for-aws-direct-connect"></a>

Trusted Advisor updated the following checks on March 29, 2022\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  AWS Direct Connect Connection Redundancy  |  Fault tolerance  |  `0t121N1Ty3`  | 
|  AWS Direct Connect Location Redundancy  |  Fault tolerance  |  `8M012Ph3U5`  | 
|  AWS Direct Connect Virtual Interface Redundancy  |  Fault tolerance  |  `4g3Nt5M1Th`  | 
+ The value for the **Region** column now shows the AWS Region code instead of the full name\. For example, resources in US East \(N\. Virginia\) will now have the `us-east-1` value\.
+ The value for the **Time Stamp** column now appears in the RFC 3339 format, such as `2022-03-30T01:02:27.000Z`\.
+ Resources that don't have any detected problems will now appear in the check table\. These resources will have a check mark icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/green.png)\) next to them\.

  Previously, only resources that Trusted Advisor recommended that you investigate appeared in the table\. These resources have a warning icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/warning.png)\) next to them\.

## AWS Security Hub controls added to the AWS Trusted Advisor console<a name="new-security-hub-controls-for-trusted-advisor"></a>

AWS Trusted Advisor added 111 Security Hub controls to the **Security** category on January 18, 2022\.

You can view your findings for Security Hub controls from the AWS Foundational Security Best Practices security standard\. This integration doesn't include controls that have the **Category: Recover > Resilience**\.

For more information about this feature, see [Viewing AWS Security Hub controls in AWS Trusted Advisor](security-hub-controls-with-trusted-advisor.md)\.

## New checks for Amazon EC2 and AWS Well\-Architected<a name="well-architected-sql-server-checks"></a>

Trusted Advisor added the following checks on December 20, 2021\.
+ Amazon EC2 instances consolidation for Microsoft SQL Server
+ Amazon EC2 instances over\-provisioned for Microsoft SQL Server
+ Amazon EC2 instances with Microsoft SQL Server end of support
+ AWS Well\-Architected high risk issues for cost optimization
+ AWS Well\-Architected high risk issues for performance
+ AWS Well\-Architected high risk issues for security
+ AWS Well\-Architected high risk issues for reliability

For more information, see the [AWS Trusted Advisor check reference](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor-check-reference.html)\.

## Updated check name for Amazon OpenSearch Service<a name="check-name-change"></a>

Trusted Advisor updated the Amazon Elasticsearch Reserved Instance Optimization check name to Amazon OpenSearch Service Reserved Instance Optimization on September 8, 2021\.

The Amazon OpenSearch Service is a successor to the Amazon Elasticsearch Service\. The check recommendations, category, and ID are the same\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  Amazon OpenSearch Service Reserved Instance Optimization  |  Cost optimization  |  `7ujm6yhn5t`  | 

**Note**  
If you use Trusted Advisor for Amazon CloudWatch metrics, the metric name for this check is also updated\. For more information, see [Creating Amazon CloudWatch alarms to monitor AWS Trusted Advisor metrics](cloudwatch-metrics-ta.md)\.

## Added checks for Amazon Elastic Block Store volume storage<a name="ebs-volume-storage-quota-checks"></a>

Trusted Advisor added the following checks on June 8, 2021\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  EBS General Purpose SSD \(gp3\) Volume Storage  |  Service limits  |  `dH7RR0l6J3`  | 
|  EBS Provisioned IOPS SSD \(io2\) Volume Storage  |  Service limits  |  `gI7MM0l7J2`  | 

## Added checks for AWS Lambda<a name="added-lambda-checks"></a>

Trusted Advisor added the following checks on March 8, 2021\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  AWS Lambda Functions with Excessive Timeouts  | Cost optimization |  `L4dfs2Q3C3`  | 
|  AWS Lambda Functions with High Error Rates  | Cost optimization |  `L4dfs2Q3C2`  | 
|  AWS Lambda Functions Using Deprecated Runtimes  | Security |  `L4dfs2Q4C5`  | 
|  AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy  | Fault tolerance |  `L4dfs2Q4C6`  | 

For more information about how to use these checks with Lambda, see [Example AWS Trusted Advisor workflow to view recommendations](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-servicemap.html#monitoring-ta-example) in the *AWS Lambda Developer Guide*\.

## Trusted Advisor check removal<a name="remove-checks-03-08-21"></a>

Trusted Advisor removed the following check for the AWS GovCloud \(US\) Region on March 8, 2021\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  EC2 Elastic IP Addresses  | Service limits |  `aW9HH0l8J6`  | 

## Updated checks for Amazon Elastic Block Store<a name="updated-checks-for-ebs-volume"></a>

Trusted Advisor updated the unit of Amazon EBS volume from gibibyte \(GiB\) to tebibyte \(TiB\) for the following checks on March 5, 2021\. 

**Note**  
If you use Trusted Advisor for Amazon CloudWatch metrics, the metric names for these five checks are also updated\. For more information, see [Creating Amazon CloudWatch alarms to monitor AWS Trusted Advisor metrics](cloudwatch-metrics-ta.md)\.


| Check name | Check category | Check ID | Updated CloudWatch metric for ServiceLimit | 
| --- | --- | --- | --- | 
|  EBS Cold HDD \(sc1\) Volume Storage  | Service limits |  `gH5CC0e3J9`  |  Cold HDD \(sc1\) volume storage \(TiB\)  | 
|  EBS General Purpose SSD \(gp2\) Volume Storage  | Service limits |  `dH7RR0l6J9`  |  General Purpose SSD \(gp2\) volume storage \(TiB\)  | 
|  EBS Magnetic \(standard\) Volume Storage  | Service limits |  `cG7HH0l7J9`  |  Magnetic \(standard\) volume storage \(TiB\)  | 
|  EBS Provisioned IOPS SSD \(io1\) Volume Storage  | Service limits |  `gI7MM0l7J9`  |  Provisioned IOPS \(SSD\) storage \(TiB\)  | 
|  EBS Throughput Optimized HDD \(st1\) Volume Storage  | Service limits |  `wH7DD0l3J9`  |  Throughput Optimized HDD \(st1\) volume storage \(TiB\)  | 

## Trusted Advisor check removal<a name="trusted-advisor-checks-removal"></a>

**Note**  
Trusted Advisor removed the following checks on November 18, 2020\.


****  

| Checks removed on November 18, 2020 | Check category | Check ID | 
| --- | --- | --- | 
|  EC2Config Service for EC2 Windows Instances  | Fault tolerance |  `V77iOLlBqz`  | 
|  ENA Driver Version for EC2 Windows Instances  | Fault tolerance |  `TyfdMXG69d`  | 
|  NVMe Driver Version for EC2 Windows Instances  | Fault tolerance |  `yHAGQJV9K5`  | 
|  PV Driver Version for EC2 Windows Instances  | Fault tolerance |  `Wnwm9Il5bG`  | 
|  EBS Active Volumes  | Service limits |  `fH7LL0l7J9`  | 

Amazon Elastic Block Store no longer has a limit on the number of volumes that you can provision\.

You can monitor your Amazon EC2 instances and verify they are up to date by using [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html), other third\-party tools, or write your own scripts to return driver information for Windows Management Instrumentation \(WMI\)\.

## Trusted Advisor check removal<a name="remove-checks-02-20-2020"></a>

Trusted Advisor removed the following check on February 18, 2020\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  Service Limits  | Performance |  `eW7HH0l7J9`  | 