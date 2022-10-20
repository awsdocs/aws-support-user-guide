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

**Alert Criteria**  
Yellow: The endpoint is active, but hasn’t been used for real\-time inference requests in the past 15 days\.

**Recommended Action**  
If the endpoint hasn’t been used in the past 15 days, we recommend that you define a scaling policy for the resource by using [Application Autoscaling\.](https://docs.aws.amazon.com/comprehend/latest/dg/comprehend-autoscaling.html)  
If the endpoint has a scaling policy defined and hasn’t been used in the past 30 days, consider deleting the endpoint and using asynchronous inference\. For more information, see [Deleting an endpoint with Amazon Comprehend](https://docs.aws.amazon.com/comprehend/latest/dg/manage-endpoints-delete.html)\.

**Report columns**  
+ Status
+ Region
+ Endpoint ARN
+ Provisioned Inference Unit
+ AutoScaling Status
+ Reason
+ Last Updated Time

## Amazon EBS over\-provisioned volumes<a name="amazon-ebs-over-provisioned-volumes"></a>

**Description**  
Checks the Amazon Elastic Block Store \(Amazon EBS\) volumes that were running at any time during the lookback period\. This check alerts you if any EBS volumes were over\-provisioned for your workloads\. When you have over\-provisioned volumes, you’re paying for unused resources\. Although some scenarios can result in low optimization by design, you can often lower your costs by changing the configuration of your EBS volumes\. Estimated monthly savings are calculated by using the current usage rate for EBS volumes\. Actual savings will vary if the volume isn’t present for a full month\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM03`

**Alert Criteria**  
 Yellow: An EBS Volume that was over\-provisioned during the lookback period\. To determine if a volume is over\-provisioned, we consider all default CloudWatch metrics \(including IOPS and throughput\)\. The algorithm used to identify over\-provisioned EBS volumes follows AWS best practices\. The algorithm is updated when a new pattern has been identified\.

**Recommended Action**  
Consider downsizing volumes that have low utilization\.  
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
+ Savings Opportunity \(%\)
+ Estimated Monthly Savings
+ Estimated Monthly Savings Currency
+ Last Updated Time

## Amazon EC2 instances consolidation for Microsoft SQL Server<a name="ec2-instances-consolidation-sql-server"></a>

**Description**  
Checks your Amazon Elastic Compute Cloud \(Amazon EC2\) instances that are running SQL Server in the past 24 hours\. This check alerts you if your instance has less than the minimum number of SQL Server licenses\. From the Microsoft SQL Server Licensing Guide, you are paying 4 vCPU licenses even if an instance has only 1 or 2 vCPUs\. You can consolidate smaller SQL Server instances to help lower costs\.   
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Qsdfp3A4L2`

**Alert Criteria**  
Yellow: An instance with SQL Server has less than 4 vCPUs\.

**Recommended Action**  
Consider consolidating smaller SQL Server workloads into instances with at least 4 vCPUs\.

**Additional Resources**  
+ [Microsoft SQL Server on AWS](http://aws.amazon.com/sql/)
+ [Microsoft Licensing on AWS](http://aws.amazon.com/windows/resources/licensing/)
+ [Microsoft SQL Server Licensing Guide](https://www.microsoft.com/en-us/sql-server/sql-server-2019-pricing)

**Report columns**  
+ Status
+ Region
+ Instance ID
+ Instance Type
+ vCPU
+ Minimum vCPU
+ SQL Server Edition
+ Last Updated Time

## Amazon EC2 instances over\-provisioned for Microsoft SQL Server<a name="ec2-instance-over-provisioned-microsoft-sql-server"></a>

**Description**  
Checks your Amazon Elastic Compute Cloud \(Amazon EC2\) instances that are running SQL Server in the past 24 hours\. An SQL Server database has a compute capacity limit for each instance\. An instance with SQL Server Standard edition can use up to 48 vCPUs\. An instance with SQL Server Web can use up to 32 vCPUs\. This check alerts you if an instance exceeds this vCPU limit\.  
If your instance is over\-provisioned, you pay full price without realizing an improvement in performance\. You can manage the number and size of your instances to help lower costs\.  
Estimated monthly savings are calculated by using the same instance family with the maximum number of vCPUs that an SQL Server instance can use and the On\-Demand pricing\. Actual savings will vary if you’re using Reserved Instances \(RI\) or if the instance isn’t running for a full day\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Qsdfp3A4L1`

**Alert Criteria**  
+ Red: An instance with SQL Server Standard edition has more than 48 vCPUs\.
+ Red: An instance with SQL Server Web edition has more than 32 vCPUs\.

**Recommended Action**  
For SQL Server Standard edition, consider changing to an instance in the same instance family with 48 vCPUs\. For SQL Server Web edition, consider changing to an instance in the same instance family with 32 vCPUs\. If it is memory intensive, consider changing to memory optimized R5 instances\. For more information, see [Best Practices for Deploying Microsoft SQL Server on Amazon EC2](https://docs.aws.amazon.com/prescriptive-guidance/latest/sql-server-ec2-best-practices/welcome.html)\.

**Additional Resources**  
+ [Microsoft SQL Server on AWS](http://aws.amazon.com/sql)
+  You can use [Launch Wizard](http://aws.amazon.com/launchwizard) to simplify your SQL Server deployment on EC2\.

**Report columns**  
+ Status
+ Region
+ Instance ID
+ Instance Type
+ vCPU
+ SQL Server Edition
+ Maximum vCPU
+ Recommended Instance Type
+ Estimated Monthly Savings
+ Last Updated Time

## Amazon EC2 Reserved Instance Lease Expiration<a name="amazon-ec2-reserved-instances-lease-expiration"></a>

**Description**  
Checks for Amazon EC2 Reserved Instances that are scheduled to expire within the next 30 days, or have expired in the preceding 30 days\.   
Reserved Instances don't renew automatically\. You can continue using an Amazon EC2 instance covered by the reservation without interruption, but you will be charged On\-Demand rates\. New Reserved Instances can have the same parameters as the expired ones, or you can purchase Reserved Instances with different parameters\.   
The estimated monthly savings is the difference between the On\-Demand and Reserved Instance rates for the same instance type\. 

**Check ID**  
`1e93e4c0b5`

**Alert Criteria**  
+ Yellow: The Reserved Instance lease expires in less than 30 days\. 
+ Yellow: The Reserved Instance lease expired in the preceding 30 days\.

**Recommended Action**  
Consider purchasing a new Reserved Instance to replace the one that is nearing the end of its term\. For more information, see [How to Purchase Reserved Instances](http://aws.amazon.com/ec2/purchasing-options/reserved-instances/buyer/) and [Buying Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-market-concepts-buying.html)\.

**Additional Resources**  
+ [Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts-on-demand-reserved-instances.html)
+ [Instance Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)

**Report columns**  
+ Status
+ Zone
+ Instance Type
+ Platform
+ Instance Count
+ Current Monthly Cost
+ Estimated Monthly Savings
+ Expiration Date
+ Reserved Instance ID
+ Reason

## Amazon EC2 Reserved Instance Optimization<a name="amazon-ec2-reserved-instances-optimization"></a>

**Description**  
An important part of using AWS involves balancing your Reserved Instance \(RI\) purchase against your On\-Demand Instance usage\. This check provides recommendations on which RIs will help reduce the costs incurred from using On\-Demand Instances\.   
We create these recommendations by analyzing your On\-Demand usage for the past 30 days\. We then categorizing the usage into eligible categories for reservations\. We simulate every combination of reservations in the generated category of usage to identify the recommended number of each type of RI to purchase\. This process of simulation and optimization allows us to maximize your cost savings\. This check covers recommendations based on Standard Reserved Instances with the partial upfront payment option\.  
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`cX3c2R1chu`

**Alert Criteria**  
Yellow: Optimizing the use of partial upfront RIs can help reduce costs\.

**Recommended Action**  
See the [Cost Explorer](http://aws.amazon.com/aws-cost-management/aws-cost-explorer/) page for more detailed and customized recommendations\. Additionally, refer to the [buying guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-market-general.html#ri-market-buying-guide) to understand how to purchase RIs and the options available\. 

**Additional Resources**  
+ Information on RIs and how they can save you money can be found [here](http://aws.amazon.com/ec2/pricing/reserved-instances/)\. 
+ For more information on this recommendation, see [Reserved Instance Optimization Check Questions](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/#Reserved_Instance_Optimization_Check_Questions) in the Trusted Advisor FAQs\.

**Report columns**  
+ Region
+ Instance Type
+ Platform
+ Recommended Number of RIs to Purchase
+ Expected Average RI Utilization
+ Estimated Savings with Recommendations \(Monthly\)
+ Upfront Cost of RIs
+ Estimated costs of RIs \(Monthly\)
+ Estimated On\-Demand Cost Post Recommended RI Purchase \(Monthly\)
+ Estimated Break Even \(Months\)
+ Lookback Period \(Days\)
+ Term \(Years\)

## Amazon ElastiCache Reserved Node Optimization<a name="amazon-elasticache-reserved-node-optimization"></a>

**Description**  
Checks your usage of ElastiCache and provides recommendations on purchase of Reserved Nodes\. These recommendations are offered to reduce the costs incurred from using ElastiCache On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Node to purchase to maximize your savings\. This check covers recommendations based on the partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`h3L1otH3re`

**Alert Criteria**  
Yellow: Optimizing the purchase of ElastiCache Reserved Nodes can help reduce costs\. 

**Recommended Action**  
See the [Cost Explorer](https://console.aws.amazon.com/billing/home?/costexplorer#/costexplorer) page for more detailed recommendations, customization options \(e\.g\. look\-back period, payment option, etc\.\) and to purchase ElastiCache Reserved Nodes\.

**Additional Resources**  
+ Information on ElastiCache Reserved Nodes and how they can save you money can be found [here](http://aws.amazon.com/elasticache/reserved-cache-nodes/)\.
+ For more information on this recommendation, see [Reserved Instance Optimization Check Questions](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/#Reserved_Instance_Optimization_Check_Questions) in the Trusted Advisor FAQs\.
+ For more detailed description of fields, see [Cost Explorer documentation](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_ReservationPurchaseRecommendationDetail.html#awscostmanagement-Type-ReservationPurchaseRecommendationDetail-AverageUtilization)

**Report columns**  
+ Region
+ Family
+ Node Type
+ Product Description
+ Recommended number of Reserved Nodes to purchase
+ Expected Average Reserved Node Utilization
+ Estimated Savings with Recommendations \(monthly\)
+ Upfront Cost of Reserved Nodes
+ Estimated cost of Reserved Nodes \(monthly\)
+ Estimated On\-Demand Cost Post Recommended Reserved Nodes Purchase \(monthly\)
+ Estimated Break Even \(months\)
+ Lookback Period \(days\)
+ Term \(years\)

## Amazon OpenSearch Service Reserved Instance Optimization<a name="amazon-elasticsearch-reserved-instance-optimization"></a>

**Description**  
Checks your usage of Amazon OpenSearch Service \(successor to Amazon Elasticsearch Service\) and provides recommendations on purchase of Reserved Instances\. These recommendations are offered to reduce the costs incurred from using OpenSearch On\-Demand\. We create these recommendations by analyzing your On\-Demand usage for the past 30 days\.   
We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to recommend the number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`7ujm6yhn5t`

**Alert Criteria**  
Yellow: Optimizing the purchase of Amazon OpenSearch Service Reserved Instances can help reduce costs\.

**Recommended Action**  
See the [Cost Explorer](https://console.aws.amazon.com/billing/home?/costexplorer#/costexplorer) page for more detailed recommendations, customization options \(e\.g\. look\-back period, payment option, etc\.\) and to purchase Amazon OpenSearch Service Reserved Instances\.

**Additional Resources**  
+ Information on Amazon OpenSearch Service Reserved Instances and how they can save you money can be found [here](https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/aes-ri.html)\.
+ For more information on this recommendation, see [Reserved Instance Optimization Check Questions](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/#Reserved_Instance_Optimization_Check_Questions) in the Trusted Advisor FAQs\.
+  For more detailed description of fields, see [Cost Explorer documentation](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_ReservationPurchaseRecommendationDetail.html#awscostmanagement-Type-ReservationPurchaseRecommendationDetail-AverageUtilization)

**Report columns**  
+ Region
+ Instance Class
+ Instance Size
+ Recommended number of Reserved Instances to purchase
+ Expected Average Reserved Instance Utilization
+ Estimated Savings with Recommendation \(monthly\)
+ Upfront Cost of Reserved Instances
+ Estimated cost of Reserved Instances \(monthly\)
+ Estimated On\-Demand Cost Post Recommended Reserved Instance Purchase \(monthly\)
+ Estimated Break Even \(months\)
+ Lookback Period \(days\)
+ Term \(years\)

## Amazon RDS Idle DB Instances<a name="amazon-rds-idle-dbs-instances"></a>

**Description**  
Checks the configuration of your Amazon Relational Database Service \(Amazon RDS\) for any database \(DB\) instances that appear to be idle\.  
If a DB instance has not had a connection for a prolonged period of time, you can delete the instance to reduce costs\. A DB instance is considered idle if the instance hasn't had a connection in the past 7 days\. If persistent storage is needed for data on the instance, you can use lower\-cost options such as taking and retaining a DB snapshot\. Manually created DB snapshots are retained until you delete them\.

**Check ID**  
`Ti39halfu8`

**Alert Criteria**  
Yellow: An active DB instance has not had a connection in the last 7 days\.

**Recommended Action**  
 Consider taking a snapshot of the idle DB instance and then either stopping it or deleting it\. Stopping the DB instance removes some of the costs for it, but does not remove storage costs\. A stopped instance keeps all automated backups based upon the configured retention period\. Stopping a DB instance usually incurs additional costs when compared to deleting the instance and then retaining only the final snapshot\. See [Stopping an Amazon RDS instance temporarily](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_StopInstance.html) and [Deleting a DB Instance with a Final Snapshot](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DeleteInstance.html)\.

**Additional Resources**  
[Back Up and Restore](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html)

**Report columns**  
+ Region
+ DB Instance Name
+ Multi\-AZ
+ Instance Type
+ Storage Provisioned \(GB\)
+ Days Since Last Connection
+ Estimated Monthly Savings \(On Demand\)

## Amazon Redshift Reserved Node Optimization<a name="amazon-redshift-reserved-node-optimization"></a>

**Description**  
Checks your usage of Amazon Redshift and provides recommendations on purchase of Reserved Nodes to help reduce costs incurred from using Amazon Redshift On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Nodes to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with a 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qw23er45t`

**Alert Criteria**  
Yellow: Optimizing the purchase of Amazon Redshift Reserved Nodes can help reduce costs\.

**Recommended Action**  
See the [Cost Explorer](https://console.aws.amazon.com/billing/home?/costexplorer#/costexplorer) page for more detailed recommendations, customization options \(e\.g\. look\-back period, payment option, etc\.\) and to purchase Amazon Redshift Reserved Nodes\.

**Additional Resources**  
+ Information on Amazon Redshift Reserved Nodes and how they can save you money can be found [here](https://docs.aws.amazon.com/redshift/latest/mgmt/purchase-reserved-node-instance.html)\.
+  For more information on this recommendation, see [Reserved Instance Optimization Check Questions](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/#Reserved_Instance_Optimization_Check_Questions) in the Trusted Advisor FAQs\.
+  For more detailed description of fields, see [Cost Explorer documentation](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_ReservationPurchaseRecommendationDetail.html#awscostmanagement-Type-ReservationPurchaseRecommendationDetail-AverageUtilization)

**Report columns**  
+ Region
+ Family
+ Node Type
+ Recommended number of Reserved Nodes to purchase
+ Expected Average Reserved Node Utilization
+ Estimated Savings with Recommendation \(monthly\)
+ UpFront Cost of Reserved Nodes
+ Estimated cost of Reserved Nodes \(monthly\)
+ Estimated On\-Demand Cost Post Recommended Reserved Nodes Purchase \(monthly\)
+ Estimated Break Even \(months\)
+ Lookback Period \(days\)
+ Term \(years\)

## Amazon Relational Database Service \(RDS\) Reserved Instance Optimization<a name="amazon-rds-reserved-instance-optimization"></a>

**Description**  
Checks your usage of RDS and provides recommendations on purchase of Reserved Instances to help reduce costs incurred from using RDS On\-Demand\.   
We generate these recommendations by analyzing your On\-Demand usage for the past 30 days\. We use this analysis to simulate every combination of reservations in the generated usage category\. This allows us to identify the best number of each type of Reserved Instance to purchase to maximize your savings\. This check covers recommendations based on partial upfront payment option with 1\-year or 3\-year commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`1qazXsw23e`

**Alert Criteria**  
Yellow: Optimizing the purchase of Amazon RDS Reserved Instances can help reduce costs\.

**Recommended Action**  
See the [Cost Explorer](https://console.aws.amazon.com/billing/home?/costexplorer#/costexplorer) page for more detailed recommendations, customization options \(e\.g\. look\-back period, payment option, etc\.\) and to purchase Amazon RDS Reserved Instances\. 

**Additional Resources**  
+ Information on Amazon RDS Reserved Instances and how they can save you money can be found [here](http://aws.amazon.com/rds/reserved-instances/)\.
+ For more information on this recommendation, see [Reserved Instance Optimization Check Questions](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/#Reserved_Instance_Optimization_Check_Questions) in the Trusted Advisor FAQs\.
+ For more detailed description of fields, see [Cost Explorer documentation](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_ReservationPurchaseRecommendationDetail.html#awscostmanagement-Type-ReservationPurchaseRecommendationDetail-AverageUtilization)

**Report columns**  
+ Region
+ Family
+ Instance Type
+ Licence Model
+ Database Edition
+ Database Engine
+ Deployment Option
+ Recommended number of Reserved Instances to purchase
+ Expected Average Reserved Instance Utilization
+ Estimated Savings with Recommendation \(monthly\)
+ Upfront Cost of Reserved Instances
+ Estimated cost of Reserved Instances \(monthly\)
+ Estimated On\-Demand Cost Post Recommended Reserve Instance Purchase \(monthly\)
+ Estimated Break Even \(months\)
+ Lookback Period \(days\)
+ Term \(years\)

## Amazon Route 53 Latency Resource Record Sets<a name="amazon-route-53-latency-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 latency record sets that are configured inefficiently\.   
To allow Amazon Route 53 to route queries to the AWS Region with the lowest network latency, you should create latency resource record sets for a particular domain name \(such as example\.com\) in different Regions\. If you create only one latency resource record set for a domain name, all queries are routed to one Region, and you pay extra for latency\-based routing without getting the benefits\.   
Hosted zones created by AWS services won’t appear in your check results\. 

**Check ID**  
`51fC20e7I2`

**Alert Criteria**  
Yellow: Only one latency resource record set is configured for a particular domain name\.

**Recommended Action**  
If you have resources in multiple regions, be sure to define a latency resource record set for each region\. See [Latency\-Based Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html#routing-policy-latency)\.  
If you have resources in only one AWS Region, consider creating resources in more than one AWS Region and define latency resource record sets for each; see [Latency\-Based Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html#routing-policy-latency)\.  
If you don't want to use multiple AWS Regions, you should use a simple resource record set\. See [Working with Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/rrsets-working-with.html)\. 

**Additional Resources**  
+ [Amazon Route 53 Developer Guide](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/)
+ [Amazon Route 53 Pricing](http://aws.amazon.com/route53/pricing/)

**Report columns**  
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Resource Record Set Type

## AWS Lambda Functions with Excessive Timeouts<a name="aws-lambda-functions-excessive-timeouts"></a>

**Description**  
Checks for Lambda functions with high timeout rates that might result in high cost\.   
Lambda charges based on run time and number of requests for your function\. Function timeouts result in errors that may cause retries\. Retrying functions will incur additionally request and run time charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q3C3`

**Alert Criteria**  
Yellow: Functions where > 10% of invocations end in an error due to a timeout on any given day within the last 7 days\.

**Recommended Action**  
Inspect function logging and X\-ray traces to determine the contributor to the high function duration\. Implement logging in your code at relevant parts, such as before or after API calls or database connections\. By default, AWS SDK clients timeouts may be longer than the configured function duration\. Adjust API and SDK connection clients to retry or fail within the function timeout\. If the expected duration is longer than the configured timeout, you can increase the timeout setting for the function\. For more information, see [Monitoring and troubleshooting Lambda applications](https://docs.aws.amazon.com/lambda/latest/dg/lambda-monitoring.html)\.

**Additional Resources**  
+ [Monitoring and troubleshooting Lambda applications](https://docs.aws.amazon.com/lambda/latest/dg/lambda-monitoring.html)
+ [Lambda Function Retry Timeout SDK](https://aws.amazon.com/premiumsupport/knowledge-center/lambda-function-retry-timeout-sdk/)
+ [Using AWS Lambda with AWS X\-Ray](https://docs.aws.amazon.com/lambda/latest/dg/services-xray.html)
+ [Accessing Amazon CloudWatch logs for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html)
+ [Error Processor Sample Application for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/samples-errorprocessor.html)

**Report columns**  
+ Status
+ Region
+ Function ARN
+ Max Daily Timeout Rate
+ Date of Max Daily Timeout Rate
+ Average Daily Timeout Rate
+ Function Timeout Settings \(millisecond\)
+ Lost Daily Compute Cost
+ Average Daily Invokes
+ Current Day Invokes
+ Current Day Timeout Rate
+ Last Updated Time

## AWS Lambda Functions with High Error Rates<a name="aws-lambda-functions-with-high-error-rates"></a>

**Description**  
Checks for Lambda functions with high error rates that might result in higher costs\.   
Lambda charges are based on the number of requests and aggregate run time for your function\. Function errors may cause retries that incur additional charges\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q3C2`

**Alert Criteria**  
Yellow: Functions where > 10% of invocations end in error on any given day within the last 7 days\.

**Recommended Action**  
Consider the following guidelines to reduce errors\. Function errors include errors returned by the function's code and errors returned by the function's runtime\.   
To help you troubleshoot Lambda errors, Lambda integrates with services like Amazon CloudWatch and AWS X\-Ray\. You can use a combination of logs, metrics, alarms, and X\-Ray tracing to quickly detect and identify issues in your function code, API, or other resources that support your application\. For more information, see [Monitoring and troubleshooting Lambda applications](https://docs.aws.amazon.com/lambda/latest/dg/lambda-monitoring.html)\.   
For more information on handling errors with specific runtimes, see [Error handling and automatic retries in AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/invocation-retries.html)\.   
For additional troubleshooting, see [Troubleshooting issues in Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-troubleshooting.html)\.   
You can also choose from an ecosystem of monitoring and observability tools provided by AWS Lambda partners\. For more information, see [AWS Lambda Partners](http://aws.amazon.com/lambda/partners/?partner-solutions-cards.sort-by=item.additionalFields.partnerNameLower&partner-solutions-cards.sort-order=asc)\.

**Additional Resources**  
+ [Error Handling and Automatic Retries in AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/invocation-retries.html)
+ [Monitoring and Troubleshooting Lambda applications](https://docs.aws.amazon.com/lambda/latest/dg/lambda-monitoring.html)
+ [Lambda Function Retry Timeout SDK](http://aws.amazon.com/premiumsupport/knowledge-center/lambda-function-retry-timeout-sdk/)
+ [Troubleshooting issues in Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-troubleshooting.html)
+ [API Invoke Errors](https://docs.aws.amazon.com/lambda/latest/dg/API_Invoke.html#API_Invoke_Errors)
+ [Error Processor Sample Application for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/samples-errorprocessor.html)

**Report columns**  
+ Status
+ Region
+ Function ARN
+ Max Daily Error Rate
+ Date for Max Error Rate
+ Average Daily Error Rate
+ Lost Daily Compute Cost
+ Average Daily Invokes
+ Current Day Invokes

  Current Day Error Rate
+ Last Updated Time

## AWS Lambda over\-provisioned functions for memory size<a name="aws-lambda-over-provisioned-functions-memory-size"></a>

**Description**  
Checks the AWS Lambda functions that were invoked at least once during the lookback period\. This check alerts you if any of your Lambda functions were over\-provisioned for memory size\. When you have Lambda functions that are over\-provisioned for memory sizes, you’re paying for unused resources\. Although some scenarios can result in low utilization by design, you can often lower your costs by changing the memory configuration of your Lambda functions\. Estimated monthly savings are calculated by using the current usage rate for Lambda functions\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`COr6dfpM05`

**Alert Criteria**  
 Yellow: A Lambda function that was over\-provisioned for memory size during the lookback period\. To determine if a Lambda function is over\-provisioned, we consider all default CloudWatch metrics for that function\. The algorithm used to identify over\-provisioned Lambda functions for memory size follows AWS best practices\. The algorithm is updated when a new pattern has been identified\.

**Recommended Action**  
 Consider reducing the memory size of your Lambda functions\.  
For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

**Report columns**  
+ Status
+ Region
+ Function Name
+ Function Version
+ Memory Size \(MB\)
+ Recommended Memory Size \(MB\)
+ Lookback Period \(days\)
+ Savings Opportunity \(%\)
+ Estimated Monthly Savings
+ Estimated Monthly Savings Currency
+ Last Updated Time

## AWS Well\-Architected high risk issues for cost optimization<a name="well-architected-high-risk-issues-cost-optimization"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the cost optimization pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L1`

**Alert Criteria**  
+ Red: At least one active high risk issue was identified in the cost optimization pillar for AWS Well\-Architected\.
+ Green: No active high risk issues were detected in the cost optimization pillar for AWS Well\-Architected\.

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
+ Number of identified HRIs for Cost Optimization
+ Number of HRIs resolved for Cost Optimization
+ Number of questions answered for Cost Optimization
+ Total number of questions in Cost Optimization pillar
+ Last Updated Time

## Idle Load Balancers<a name="idle-load-balancers"></a>

**Description**  
Checks your Elastic Load Balancing configuration for load balancers that are idle\.   
Any load balancer that is configured accrues charges\. If a load balancer has no associated back\-end instances, or if network traffic is severely limited, the load balancer is not being used effectively\. This check currently only checks for Classic Load Balancer type within ELB service\. It does not include other ELB types \(Application Load Balancer, Network Load Balancer\)\.

**Check ID**  
`hjLMh88uM8`

**Alert Criteria**  
+ Yellow: A load balancer has no active back\-end instances\.
+ Yellow: A load balancer has no healthy back\-end instances\.
+ Yellow: A load balancer has had less than 100 requests per day for the last 7 days\.

**Recommended Action**  
If your load balancer has no active back\-end instances, consider registering instances or deleting your load balancer\. See [Registering Your Amazon EC2 Instances with Your Load Balancer](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/US_DeReg_Reg_Instances.html#RegisteringInstances) or [Delete Your Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-getting-started.html#delete-load-balancer)\.  
If your load balancer has no healthy back\-end instances, see [Troubleshooting Elastic Load Balancing: Health Check Configuration](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/ts-elb-healthcheck.html)\.  
If your load balancer has had a low request count, consider deleting your load balancer\. See [Delete Your Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-getting-started.html#delete-load-balancer)\.

**Additional Resources**  
+ [Managing Load Balancers](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/UserScenarios.html)
+ [Troubleshoot Elastic Load Balancing](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/elb-troubleshooting.html)

**Report columns**  
+ Region
+ Load Balancer Name
+ Reason
+ Estimated Monthly Savings

## Low Utilization Amazon EC2 Instances<a name="low-utilization-amazon-ec2-instances"></a>

**Description**  
Checks the Amazon Elastic Compute Cloud \(Amazon EC2\) instances that were running at any time during the last 14 days\. This check alerts you if the daily CPU utilization was 10% or less and network I/O was 5 MB or less for at least 4 days\.  
Running instances generate hourly usage charges\. Although some scenarios can result in low utilization by design, you can often lower your costs by managing the number and size of your instances\.   
Estimated monthly savings are calculated by using the current usage rate for On\-Demand Instances and the estimated number of days the instance might be underutilized\. Actual savings will vary if you are using Reserved Instances or Spot Instances, or if the instance is not running for a full day\. To get daily utilization data, download the report for this check\. 

**Check ID**  
`Qch7DwouX1`

**Alert Criteria**  
Yellow: An instance had 10% or less daily average CPU utilization and 5 MB or less network I/O on at least 4 of the previous 14 days\.

**Recommended Action**  
Consider stopping or terminating instances that have low utilization, or scale the number of instances by using Auto Scaling\. For more information, see [Stop and Start Your Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html), [Terminate Your Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html), and [What is Auto Scaling?](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/WhatIsAutoScaling.html)

**Additional Resources**  
+ [Monitoring Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-monitoring.html)
+ [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AESDG-chapter-instancedata.html)
+ [Amazon CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)
+ [Auto Scaling Developer Guide](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/WhatIsAutoScaling.html)

**Report columns**  
+ Region/AZ
+ Instance ID
+ Instance Name
+ Instance Type
+ Estimated Monthly Savings
+ CPU Utilization 14\-day Average
+ Network I/O 14\-Day Average
+ Number of Days Low Utilization

## Savings Plan<a name="savings-plan"></a>

**Description**  
Checks your usage of Amazon EC2, Fargate, and Lambda over the last 30 days and provides Savings Plan purchase recommendations\. These recommendations allow you to commit to a consistent usage amount measured in dollars per hour for a one\- or three\-year term in exchange for discounted rates\.   
These are sourced from AWS Cost Explorer, which can get more detailed recommendation information\. You can also purchase a savings pan through Cost Explorer\. These recommendations should be considered an alternative to your RI recommendations\. We suggest that you act on one set of recommendations only\. Acting on both sets can lead to over\-commitment\.   
This check is not available to accounts linked in consolidated billing\. The recommendations for this check are only available for the paying account\.

**Check ID**  
`vZ2c2W1srf`

**Alert Criteria**  
Yellow: Optimizing the purchase of Savings Plans can help reduce costs\. 

**Recommended Action**  
See the [Cost Explorer](https://console.aws.amazon.com/billing/home?/costexplorer#/costexplorer/) page for more detailed and customized recommendations and to purchase Savings Plans\.

**Additional Resources**  
+  [Savings Plan User Guide](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html)
+ Savings Plans [FAQ](http://aws.amazon.com/savingsplans/faq/)

**Report columns**  
+ Savings Plan type
+ Payment option
+ Upfront cost
+ Hourly commitment to purchase
+ Estimated average utilization
+ Estimated monthly savings
+ Estimated savings percentage
+ Term \(Years\)
+ Lookback Period \(Days\)

## Unassociated Elastic IP Addresses<a name="unassociated-elastic-ip-addresses"></a>

**Description**  
Checks for Elastic IP addresses \(EIPs\) that are not associated with a running Amazon Elastic Compute Cloud \(Amazon EC2\) instance\.   
EIPs are static IP addresses designed for dynamic cloud computing\. Unlike traditional static IP addresses, EIPs mask the failure of an instance or Availability Zone by remapping a public IP address to another instance in your account\. A nominal charge is imposed for an EIP that is not associated with a running instance\.

**Check ID**  
`Z4AUBRNSmz`

**Alert Criteria**  
Yellow: An allocated Elastic IP address \(EIP\) is not associated with a running Amazon EC2 instance\.

**Recommended Action**  
 Associate the EIP with a running active instance, or release the unassociated EIP\. For more information, see [Associating an Elastic IP Address with a Different Running Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#using-instance-addressing-eips-associating-different) and [Releasing an Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#using-instance-addressing-eips-releasing)\.

**Additional Resources**  
[Elastic IP Addresses](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)

**Report columns**  
+ Region
+ IP Address

## Underutilized Amazon EBS Volumes<a name="underutilized-amazon-ebs-volumes"></a>

**Description**  
Checks Amazon Elastic Block Store \(Amazon EBS\) volume configurations and warns when volumes appear to be underutilized\.   
Charges begin when a volume is created\. If a volume remains unattached or has very low write activity \(excluding boot volumes\) for a period of time, the volume is underutilized\. We recommend that you remove underutilized volumes to reduce costs\.

**Check ID**  
`DAvU99Dc4C`

**Alert Criteria**  
Yellow: A volume is unattached or had less than 1 IOPS per day for the past 7 days\.

**Recommended Action**  
Consider creating a snapshot and deleting the volume to reduce costs\. For more information, see [Creating an Amazon EBS Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-snapshot.html) and [Deleting an Amazon EBS Volume](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-deleting-volume.html)\.

**Additional Resources**  
+ [Amazon Elastic Block Store \(Amazon EBS\)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
+ [Monitoring the Status of Your Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring-volume-status.html)

**Report columns**  
+ Region
+ Volume ID
+ Volume Name
+ Volume Type
+ Volume Size
+ Monthly Storage Cost
+ Snapshot ID
+ Snapshot Name
+ Snapshot Age

**Note**  
If you opted in your account for AWS Compute Optimizer, we recommend that you use the Amazon EBS over\-provisioned volumes check instead\. For more information, see [Opt in AWS Compute Optimizer for Trusted Advisor checks](compute-optimizer-with-trusted-advisor.md)\.

## Underutilized Amazon Redshift Clusters<a name="underutilized-amazon-redshift-clusters"></a>

**Description**  
Checks your Amazon Redshift configuration for clusters that appear to be underutilized\.   
If an Amazon Redshift cluster has not had a connection for a prolonged period of time, or is using a low amount of CPU, you can use lower\-cost options such as downsizing the cluster, or shutting down the cluster and taking a final snapshot\. Final snapshots are retained even after you delete your cluster\.

**Check ID**  
`G31sQ1E9U`

**Alert Criteria**  
+ Yellow: A running cluster has not had a connection in the last 7 days\.
+ Yellow: A running cluster had less than 5% cluster\-wide average CPU utilization for 99% of the last 7 days\.

**Recommended Action**  
Consider shutting down the cluster and taking a final snapshot, or downsizing the cluster\. See [Shutting Down and Deleting Clusters](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html#rs-mgmt-shutdown-delete-cluster) and [Resizing a Cluster](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html#cluster-resize-intro)\.

**Additional Resources**  
[Amazon CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/)

**Report columns**  
+ Status
+ Region
+ Cluster
+ Instance Type
+ Reason
+ Estimated Monthly Savings