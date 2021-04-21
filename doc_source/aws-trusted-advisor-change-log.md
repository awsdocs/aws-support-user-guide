# Change log for AWS Trusted Advisor checks<a name="aws-trusted-advisor-change-log"></a>

See the following topic for recent changes to Trusted Advisor checks\. 

**Note**  
If you use the Trusted Advisor console or the AWS Support API, checks that were removed won't appear in check results\. If you use any of the removed checks such as specifying the check ID in an AWS Support API operation or your code, you must remove these checks to avoid API call errors\.

For more information about the available checks, see the [AWS Trusted Advisor best practice checklist](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practice-checklist/)\.

## Added checks for AWS Lambda<a name="added-lambda-checks"></a>

Trusted Advisor added the following checks on March 8, 2021\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  AWS Lambda Functions with Excessive Timeouts  | Cost Optimization |  L4dfs2Q3C3  | 
|  AWS Lambda Functions with High Error Rates  | Cost Optimization |  L4dfs2Q3C2  | 
|  AWS Lambda Functions Using Deprecated Runtimes  | Security |  L4dfs2Q4C5  | 
|  AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy  | Fault Tolerance |  L4dfs2Q4C6  | 

For more information about how to use these checks with Lambda, see [Example AWS Trusted Advisor workflow to view recommendations](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-servicemap.html#monitoring-ta-example) in the *AWS Lambda Developer Guide*\.

## Trusted Advisor check removal<a name="remove-checks-03-08-21"></a>

Trusted Advisor removed the following check for the AWS GovCloud \(US\) Region on March 8, 2021\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  EC2 Elastic IP Addresses  | Service Limits |  aW9HH0l8J6  | 

## Updated checks for Amazon Elastic Block Store<a name="updated-checks-for-ebs-volume"></a>

Trusted Advisor updated the unit of Amazon EBS volume from gibibyte \(GiB\) to tebibyte \(TiB\) for the following checks on March 5, 2021\. 

**Note**  
If you use Trusted Advisor for Amazon CloudWatch metrics, the metric names for these five checks are also updated\. For more information, see [Creating Trusted Advisor alarms using CloudWatch](cloudwatch-metrics-ta.md)\.


| Check name | Check category | Check ID | Updated CloudWatch metric for ServiceLimit | 
| --- | --- | --- | --- | 
|  EBS Cold HDD \(sc1\) Volume Storage  | Service Limits |  gH5CC0e3J9  |  Cold HDD \(sc1\) volume storage \(TiB\)  | 
|  EBS General Purpose SSD \(gp2\) Volume Storage  | Service Limits |  dH7RR0l6J9  |  General Purpose SSD \(gp2\) volume storage \(TiB\)  | 
|  EBS Magnetic \(standard\) Volume Storage  | Service Limits |  cG7HH0l7J9  |  Magnetic \(standard\) volume storage \(TiB\)  | 
|  EBS Provisioned IOPS SSD \(io1\) Volume Storage  | Service Limits |  gI7MM0l7J9  |  Provisioned IOPS \(SSD\) storage \(TiB\)  | 
|  EBS Throughput Optimized HDD \(st1\) Volume Storage  | Service Limits |  wH7DD0l3J9  |  Throughput Optimized HDD \(st1\) volume storage \(TiB\)  | 

## Trusted Advisor check removal<a name="trusted-advisor-checks-removal"></a>

**Note**  
Trusted Advisor removed the following checks on November 18, 2020\.


****  

| Checks removed on November 18, 2020 | Check category | Check ID | 
| --- | --- | --- | 
|  EC2Config Service for EC2 Windows Instances  | Fault Tolerance |  V77iOLlBqz  | 
|  ENA Driver Version for EC2 Windows Instances  | Fault Tolerance |  TyfdMXG69d  | 
|  NVMe Driver Version for EC2 Windows Instances  | Fault Tolerance |  yHAGQJV9K5  | 
|  PV Driver Version for EC2 Windows Instances  | Fault Tolerance |  Wnwm9Il5bG  | 
|  EBS Active Volumes  | Service Limits |  fH7LL0l7J9  | 

Amazon Elastic Block Store no longer has a limit on the number of volumes that you can provision\.

You can monitor your Amazon EC2 instances and verify they are up to date by using [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html), other third\-party tools, or write your own scripts to return driver information for Windows Management Instrumentation \(WMI\)\.

## Trusted Advisor check removal<a name="remove-checks-02-20-2020"></a>

Trusted Advisor removed the following check on February 18, 2020\.


| Check name | Check category | Check ID | 
| --- | --- | --- | 
|  Service Limits  | Performance |  eW7HH0l7J9  | 