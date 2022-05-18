# Cost optimization<a name="cost-optimization-checks"></a>

You can use the following checks for the cost optimization category\.

**Contents**
+ [Amazon Comprehend Underutilized Endpoints](#amazon-comprehend-underutilized-endpoints)
+ [Amazon EBS over\-provisioned volumes](#amazon-ebs-over-provisioned-volumes)
+ [Amazon EC2 instances consolidation for Microsoft SQL Server](#ec2-instances-consolidation-sql-server)
+ [Amazon EC2 instances over\-provisioned for Microsoft SQL Server](#ec2-instance-over-provisioned-microsoft-sql-server)
+ [Amazon EC2 Reserved Instance Lease Expiration](#amazon-ec2-reserved-instances-lease-expiration)
+ [Amazon EC2 Reserved Instance Optimization](#amazon-ec2-reserved-instances-optimization)
+ [Amazon ElastiCache Reserved Node Optimization](#amazon-elasticache-reserved-node-optimization)
+ [Amazon OpenSearch Service Reserved Instance Optimization](#amazon-elasticsearch-reserved-instance-optimization)
+ [Amazon RDS Idle DB Instances](#amazon-rds-idle-dbs-instances)
+ [Amazon Redshift Reserved Node Optimization](#amazon-redshift-reserved-node-optimization)
+ [Amazon Relational Database Service \(RDS\) Reserved Instance Optimization](#amazon-rds-reserved-instance-optimization)
+ [Amazon Route 53 Latency Resource Record Sets](#amazon-route-53-latency-resource-record-sets)
+ [AWS Lambda Functions with Excessive Timeouts](#aws-lambda-functions-excessive-timeouts)
+ [AWS Lambda Functions with High Error Rates](#aws-lambda-functions-with-high-error-rates)
+ [AWS Lambda over\-provisioned functions for memory size](#aws-lambda-over-provisioned-functions-memory-size)
+ [AWS Well\-Architected high risk issues for cost optimization](#well-architected-high-risk-issues-cost-optimization)
+ [Idle Load Balancers](#idle-load-balancers)
+ [Low Utilization Amazon EC2 Instances](#low-utilization-amazon-ec2-instances)
+ [Savings Plan](#savings-plan)
+ [Unassociated Elastic IP Addresses](#unassociated-elastic-ip-addresses)
+ [Underutilized Amazon EBS Volumes](#underutilized-amazon-ebs-volumes)
+ [Underutilized Amazon Redshift Clusters](#underutilized-amazon-redshift-clusters)

## Amazon Comprehend Underutilized Endpoints<a name="amazon-comprehend-underutilized-endpoints"></a>

**Description**  
Checks the throughput configuration of your endpoints\. This check alerts you when endpoints are not actively used for real\-time inference requests\. An endpoint that isn’t used for more than 15 consecutive days is considered underutilized\. All endpoints accrue charges based on both the throughput set, and the length of time that the endpoint is active\.   
This check is automatically refreshed once a day\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Cm24dfsM12`

## Amazon EBS over\-provisioned volumes<a name="amazon-ebs-over-provisioned-volumes"></a>

**Description**  
Checks the Amazon Elastic Block Store \(Amazon EBS\) volumes that were running at any time during the lookback period\. This check alerts you if any EBS volumes were over\-provisioned for your workloads\. When you have over\-provisioned volumes, you’re paying for unused resources\. Although some scenarios can result in low optimization by design, you can often lower your costs by changing the configuration of your EBS volumes\. Estimated monthly savings are calculated by using the current usage rate for EBS volumes\. Actual savings will vary if the volume isn’t present for a full month\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM03`

## Amazon EC2 instances consolidation for Microsoft SQL Server<a name="ec2-instances-consolidation-sql-server"></a>

**Description**  
Checks your Amazon Elastic Compute Cloud \(Amazon EC2\) instances that are running SQL Server in the past 24 hours\. This check alerts you if your instance has less than the minimum number of SQL Server licenses\. From the Microsoft SQL Server Licensing Guide, you are paying 4 vCPU licenses even if an instance has only 1 or 2 vCPUs\. You can consolidate smaller SQL Server instances to help lower costs\.   
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Qsdfp3A4L2`

## Amazon EC2 instances over\-provisioned for Microsoft SQL Server<a name="ec2-instance-over-provisioned-microsoft-sql-server"></a>

**Description**  
Checks your Amazon Elastic Compute Cloud \(Amazon EC2\) instances that are running SQL Server in the past 24 hours\. An SQL Server database has a compute capacity limit for each instance\. An instance with SQL Server Standard edition can use up to 48 vCPUs\. An instance with SQL Server Web can use up to 32 vCPUs\. This check alerts you if an instance exceeds this vCPU limit\.  
If your instance is over\-provisioned, you pay full price without realizing an improvement in performance\. You can manage the number and size of your instances to help lower costs\.  
Estimated monthly savings are calculated by using the same instance family with the maximum number of vCPUs that an SQL Server instance can use and the On\-Demand pricing\. Actual savings will vary if you’re using Reserved Instances \(RI\) or if the instance isn’t running for a full day\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Qsdfp3A4L1`

## Amazon EC2 Reserved Instance Lease Expiration<a name="amazon-ec2-reserved-instances-lease-expiration"></a>

**Description**  
Checks for Amazon EC2 Reserved Instances that are scheduled to expire within the next 30 days, or have expired in the preceding 30 days\.   
Reserved Instances don't renew automatically\. You can continue using an Amazon EC2 instance covered by the reservation without interruption, but you will be charged On\-Demand rates\. New Reserved Instances can have the same parameters as the expired ones, or you can purchase Reserved Instances with different parameters\.   
The estimated monthly savings is the difference between the On\-Demand and Reserved Instance rates for the same instance type\. 

**Check ID**  
`1e93e4c0b5`

## Amazon EC2 Reserved Instance Optimization<a name="amazon-ec2-reserved-instances-optimization"></a>

**Description**  
An important part of using AWS involves balancing your Reserved Instance \(RI\) purchase against your On\-Demand Instance usage\. This check provides recommendations on which RIs will help reduce the costs incurred from using On\-Demand Instances\.   
We create these recommendations by analyzing your On\-Demand usage for the past 30 days\. We then categorizing the usage into eligible categories for reservations\. We simulate every combination of reservations in the generated category of usage to identify the recommended number of each type of RI to purchase\. This process of simulation and optimization allows us to maximize your cost savings\. This check covers recommendations based on Standard Reserved Instances with the partial upfront payment option\.  
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`cX3c2R1chu`

## Amazon ElastiCache Reserved Node Optimization<a name="amazon-elasticache-reserved-node-optimization"></a>

**Description**  
Checks your usage of ElastiCache and provides recommendations on purchase of Reserved Nodes\. These recommendations are offered to reduce the costs incurred from using ElastiCache On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Node to purchase to maximize your savings\. This check covers recommendations based on the partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`h3L1otH3re`

## Amazon OpenSearch Service Reserved Instance Optimization<a name="amazon-elasticsearch-reserved-instance-optimization"></a>

**Description**  
Checks your usage of Amazon OpenSearch Service \(successor to Amazon Elasticsearch Service\) and provides recommendations on purchase of Reserved Instances\. These recommendations are offered to reduce the costs incurred from using OpenSearch On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`7ujm6yhn5t`

## Amazon RDS Idle DB Instances<a name="amazon-rds-idle-dbs-instances"></a>

**Description**  
Checks the configuration of your Amazon Relational Database Service \(Amazon RDS\) for any database \(DB\) instances that appear to be idle\.  
If a DB instance has not had a connection for a prolonged period of time, you can delete the instance to reduce costs\. A DB instance is considered idle if the instance hasn't had a connection in the past 7 days\. If persistent storage is needed for data on the instance, you can use lower\-cost options such as taking and retaining a DB snapshot\. Manually created DB snapshots are retained until you delete them\.

**Check ID**  
`Ti39halfu8`

## Amazon Redshift Reserved Node Optimization<a name="amazon-redshift-reserved-node-optimization"></a>

**Description**  
Checks your usage of Amazon Redshift and provides recommendations on purchase of Reserved Nodes to help reduce costs incurred from using Amazon Redshift On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Nodes to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qw23er45t`

## Amazon Relational Database Service \(RDS\) Reserved Instance Optimization<a name="amazon-rds-reserved-instance-optimization"></a>

**Description**  
Checks your usage of RDS and provides recommendations on purchase of Reserved Instances to help reduce costs incurred from using RDS On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qazXsw23e`

## Amazon Route 53 Latency Resource Record Sets<a name="amazon-route-53-latency-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 latency record sets that are configured inefficiently\.   
To allow Amazon Route 53 to route queries to the AWS Region with the lowest network latency, you should create latency resource record sets for a particular domain name \(such as example\.com\) in different Regions\. If you create only one latency resource record set for a domain name, all queries are routed to one Region, and you pay extra for latency\-based routing without getting the benefits\.   
Hosted zones created by AWS services won’t appear in your check results\. 

**Check ID**  
`51fC20e7I2`

## AWS Lambda Functions with Excessive Timeouts<a name="aws-lambda-functions-excessive-timeouts"></a>

**Description**  
Checks for Lambda functions with high timeout rates that might result in high cost\.   
Lambda charges based on run time and number of requests for your function\. Function timeouts result in errors that may cause retries\. Retrying functions will incur additionally request and run time charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q3C3`

## AWS Lambda Functions with High Error Rates<a name="aws-lambda-functions-with-high-error-rates"></a>

**Description**  
Checks for Lambda functions with high error rates that might result in higher costs\.   
Lambda charges are based on the number of requests and aggregate run time for your function\. Function errors may cause retries that incur additional charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q3C2`

## AWS Lambda over\-provisioned functions for memory size<a name="aws-lambda-over-provisioned-functions-memory-size"></a>

**Description**  
Checks the AWS Lambda functions that were invoked at least once during the lookback period\. This check alerts you if any of your Lambda functions were over\-provisioned for memory size\. When you have Lambda functions that are over\-provisioned for memory sizes, you’re paying for unused resources\. Although some scenarios can result in low utilization by design, you can often lower your costs by changing the memory configuration of your Lambda functions\. Estimated monthly savings are calculated by using the current usage rate for Lambda functions\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM05`

## AWS Well\-Architected high risk issues for cost optimization<a name="well-architected-high-risk-issues-cost-optimization"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the cost optimization pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L1`

## Idle Load Balancers<a name="idle-load-balancers"></a>

**Description**  
Checks your Elastic Load Balancing configuration for load balancers that are idle\.   
Any load balancer that is configured accrues charges\. If a load balancer has no associated back\-end instances, or if network traffic is severely limited, the load balancer is not being used effectively\. This check currently only checks for Classic Load Balancer type within ELB service\. It does not include other ELB types \(Application Load Balancer, Network Load Balancer\)\.

**Check ID**  
`hjLMh88uM8`

## Low Utilization Amazon EC2 Instances<a name="low-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. This check alerts you if the daily CPU utilization was 10% or less and network I/O was 5 MB or less for at least 4 days\.  
Running instances generate hourly usage charges\. Although some scenarios can result in low utilization by design, you can often lower your costs by managing the number and size of your instances\.   
Estimated monthly savings are calculated by using the current usage rate for On\-Demand Instances and the estimated number of days the instance might be underutilized\. Actual savings will vary if you are using Reserved Instances or Spot Instances, or if the instance is not running for a full day\. To get daily utilization data, download the report for this check\. 

**Check ID**  
`Qch7DwouX1`

## Savings Plan<a name="savings-plan"></a>

**Description**  
Checks your usage of Amazon EC2, Fargate, and Lambda over the last 30 days and provides Savings Plan purchase recommendations\. These recommendations allow you to commit to a consistent usage amount measured in dollars per hour for a one\- or three\-year term in exchange for discounted rates\.   
These are sourced from AWS Cost Explorer, which can get more detailed recommendation information\. You can also purchase a savings pan through Cost Explorer\. These recommendations should be considered an alternative to your RI recommendations\. We suggest that you act on one set of recommendations only\. Acting on both sets can lead to over\-commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`vZ2c2W1srf`

## Unassociated Elastic IP Addresses<a name="unassociated-elastic-ip-addresses"></a>

**Description**  
Checks for Elastic IP addresses \(EIPs\) that are not associated with a running Amazon Elastic Compute Cloud \(Amazon EC2\) instance\.   
EIPs are static IP addresses designed for dynamic cloud computing\. Unlike traditional static IP addresses, EIPs mask the failure of an instance or Availability Zone by remapping a public IP address to another instance in your account\. A nominal charge is imposed for an EIP that is not associated with a running instance\.

**Check ID**  
`Z4AUBRNSmz`

## Underutilized Amazon EBS Volumes<a name="underutilized-amazon-ebs-volumes"></a>

**Description**  
Checks Amazon Elastic Block Store \(Amazon EBS\) volume configurations and warns when volumes appear to be underutilized\.   
Charges begin when a volume is created\. If a volume remains unattached or has very low write activity \(excluding boot volumes\) for a period of time, the volume is underutilized\. We recommend that you remove underutilized volumes to reduce costs\.

**Check ID**  
`DAvU99Dc4C`

**Note**  
If you opted in your account for AWS Compute Optimizer, we recommend that you use the Amazon EBS over\-provisioned volumes check instead\. For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

## Underutilized Amazon Redshift Clusters<a name="underutilized-amazon-redshift-clusters"></a>

**Description**  
Checks your Amazon Redshift configuration for clusters that appear to be underutilized\.   
If an Amazon Redshift cluster has not had a connection for a prolonged period of time, or is using a low amount of CPU, you can use lower\-cost options such as downsizing the cluster, or shutting down the cluster and taking a final snapshot\. Final snapshots are retained even after you delete your cluster\.

**Check ID**  
`G31sQ1E9U`