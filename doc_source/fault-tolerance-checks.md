# Fault tolerance<a name="fault-tolerance-checks"></a>

You can use the following checks for the fault tolerance category\.

**Contents**
+ [Amazon Aurora DB Instance Accessibility](#amazon-aurora-db-instance-accessibility)
+ [Amazon Comprehend Endpoint Access Risk](#amazon-comprehend-endpoint-access-risk)
+ [Amazon EBS Snapshots](#amazon-ebs-snapshots)
+ [Amazon EC2 Availability Zone Balance](#amazon-ecs-availability-zone-balance)
+ [Amazon RDS Backups](#amazon-rds-backups)
+ [Amazon RDS Multi\-AZ](#amazon-rds-multi-az)
+ [Amazon Route 53 Deleted Health Checks](#amazon-route-53-deleted-health-checks)
+ [Amazon Route 53 Failover Resource Record Sets](#amazon-route-53-failover-resource-record-sets)
+ [Amazon Route 53 High TTL Resource Record Sets](#amazon-route-53-high-ttl-resource-record-sets)
+ [Amazon Route 53 Name Server Delegations](#amazon-route-53-name-server-delegations)
+ [Amazon S3 Bucket Logging](#amazon-s3-bucket-logging)
+ [Amazon S3 Bucket Versioning](#amazon-s3-bucket-versioning)
+ [Auto Scaling Group Health Check](#auto-scaling-group-health-check)
+ [Auto Scaling Group Resources](#auto-scaling-group-resources)
+ [AWS Direct Connect Connection Redundancy](#aws-direct-connect-connection-redundancy)
+ [AWS Direct Connect Location Redundancy](#aws-direct-connect-location-redundancy)
+ [AWS Direct Connect Virtual Interface Redundancy](#aws-direct-connect-virtual-interface-redundancy)
+ [AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy](#aws-lambda-vpc-enabled-functions-without-multi-az-redundancy)
+ [AWS Well\-Architected high risk issues for reliability](#well-architected-high-risk-issues-reliability)
+ [ELB Connection Draining](#elb-connection-draining)
+ [ELB Cross\-Zone Load Balancing](#elb-cross-zone-load-balancing)
+ [Load Balancer Optimization](#load-balancer-optimization)
+ [VPN Tunnel Redundancy](#vpn-tunnel-redundancy)

## Amazon Aurora DB Instance Accessibility<a name="amazon-aurora-db-instance-accessibility"></a>

**Description**  
Checks for cases where an Amazon Aurora DB cluster has both private and public instances\.   
When your primary instance fails, a replica can be promoted to a primary instance\. If that replica is private, users who have only public access would no longer be able to connect to the database after failover\. We recommend that all the DB instances in a cluster have the same accessibility\.

**Check ID**  
`xuy7H1avtl`

## Amazon Comprehend Endpoint Access Risk<a name="amazon-comprehend-endpoint-access-risk"></a>

**Description**  
Checks the AWS Key Management Service \(AWS KMS\) key permissions for an endpoint where the underlying model was encrypted by using customer managed keys\. If the customer managed key is disabled, or the key policy was changed to alter the allowed permissions for Amazon Comprehend, the endpoint availability might be affected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Cm24dfsM13`

## Amazon EBS Snapshots<a name="amazon-ebs-snapshots"></a>

**Description**  
Checks the age of the snapshots for your Amazon Elastic Block Store \(Amazon EBS\) volumes \(either available or in\-use\)\.   
Even though Amazon EBS volumes are replicated, failures can occur\. Snapshots are persisted to Amazon Simple Storage Service \(Amazon S3\) for durable storage and point\-in\-time recovery\.

**Check ID**  
`H7IgTzjTYb`

## Amazon EC2 Availability Zone Balance<a name="amazon-ecs-availability-zone-balance"></a>

**Description**  
Checks the distribution of Amazon Elastic Compute Cloud \(Amazon EC2\) instances across Availability Zones in a Region\.   
Availability Zones are distinct locations that are insulated from failures in other Availability Zones\. This allows inexpensive, low\-latency network connectivity between Availability Zones in the same Region\. By launching instances in multiple Availability Zones in the same Region, you can help protect your applications from a single point of failure\.

**Check ID**  
`wuy7G1zxql`

## Amazon RDS Backups<a name="amazon-rds-backups"></a>

**Description**  
Checks for automated backups of Amazon RDS DB instances\.   
By default, backups are enabled with a retention period of one day\. Backups reduce the risk of unexpected data loss and allow for point\-in\-time recovery\. 

**Check ID**  
`opQPADkZvH`

## Amazon RDS Multi\-AZ<a name="amazon-rds-multi-az"></a>

**Description**  
Checks for DB instances that are deployed in a single Availability Zone \(AZ\)\.   
Multi\-AZ deployments enhance database availability by synchronously replicating to a standby instance in a different Availability Zone\. During planned database maintenance, or the failure of a DB instance or Availability Zone, Amazon RDS automatically fails over to the standby\. This failover allows database operations to resume quickly without administrative intervention\. Because Amazon RDS does not support Multi\-AZ deployment for Microsoft SQL Server, this check does not examine SQL Server instances\.

**Check ID**  
`f2iK5R6Dep`

## Amazon Route 53 Deleted Health Checks<a name="amazon-route-53-deleted-health-checks"></a>

**Description**  
Checks for resource record sets that are associated with health checks that have been deleted\.  
Route 53 does not prevent you from deleting a health check that is associated with one or more resource record sets\. If you delete a health check without updating the associated resource record sets, the routing of DNS queries for your DNS failover configuration will not work as intended\.   
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`Cb877eB72b`

## Amazon Route 53 Failover Resource Record Sets<a name="amazon-route-53-failover-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 failover resource record sets that have a misconfiguration\.   
When Amazon Route 53 health checks determine that the primary resource is unhealthy, Amazon Route 53 responds to queries with a secondary, backup resource record set\. You must create correctly configured primary and secondary resource record sets for failover to work\.   
Hosted zones created by AWS services won't appear in your check results\. 

**Check ID**  
`b73EEdD790`

## Amazon Route 53 High TTL Resource Record Sets<a name="amazon-route-53-high-ttl-resource-record-sets"></a>

**Description**  
Checks for resource record sets that can benefit from having a lower time\-to\-live \(TTL\) value\.   
TTL is the number of seconds that a resource record set is cached by DNS resolvers\. When you specify a long TTL, DNS resolvers take longer to request updated DNS records, which can cause unnecessary delay in rerouting traffic\. For example, a long TTL creates a delay between when DNS Failover detects an endpoint failure, and when it responds by rerouting traffic\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`C056F80cR3`

## Amazon Route 53 Name Server Delegations<a name="amazon-route-53-name-server-delegations"></a>

**Description**  
Checks for Amazon Route 53 hosted zones for which your domain registrar or DNS is not using the correct Route 53 name servers\.   
When you create a hosted zone, Route 53 assigns a delegation set of four name servers\. The names of these servers are ns\-*\#\#\#*\.awsdns\-*\#\#*\.com, \.net, \.org, and \.co\.uk, where *\#\#\#* and *\#\#* typically represent different numbers\. Before Route 53 can route DNS queries for your domain, you must update your registrar's name server configuration to remove the name servers that the registrar assigned\. Then, you must add all four name servers in the Route 53 delegation set\. For maximum availability, you must add all four Route 53 name servers\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`cF171Db240`

## Amazon S3 Bucket Logging<a name="amazon-s3-bucket-logging"></a>

**Description**  
Checks the logging configuration of Amazon Simple Storage Service \(Amazon S3\) buckets\.   
When server access logging is enabled, detailed access logs are delivered hourly to a bucket that you choose\. An access log record contains details about each request, such as the request type, the resources specified in the request, and the time and date the request was processed\. By default, bucket logging is not enabled\. You should enable logging if you want to perform security audits or learn more about users and usage patterns\.  
When logging is initially enabled, the configuration is automatically validated\. However, future modifications can result in logging failures\. This check examines explicit Amazon S3 bucket permissions, but it does not examine associated bucket policies that might override the bucket permissions\.

**Check ID**  
`BueAdJ7NrP`

## Amazon S3 Bucket Versioning<a name="amazon-s3-bucket-versioning"></a>

**Description**  
Checks for Amazon Simple Storage Service buckets that do not have versioning enabled, or that have versioning suspended\.   
When versioning is enabled, you can easily recover from both unintended user actions and application failures\. Versioning allows you to preserve, retrieve, and restore any version of any object stored in a bucket\. You can use lifecycle rules to manage all versions of your objects, as well as their associated costs, by automatically archiving objects to the Glacier storage class\. Rules can also be configured to remove versions of your objects after a specified period of time\. You can also require multi\-factor authentication \(MFA\) for any object deletions or configuration changes to your buckets\.   
Versioning can't be deactivated after it has been enabled\. However, it can be suspended, which prevents new versions of objects from being created\. Using versioning can increase your costs for Amazon S3, because you pay for storage of multiple versions of an object\.

**Check ID**  
`R365s2Qddf`

## Auto Scaling Group Health Check<a name="auto-scaling-group-health-check"></a>

**Description**  
Examines the health check configuration for Auto Scaling groups\.   
If Elastic Load Balancing is being used for an Auto Scaling group, the recommended configuration is to enable an Elastic Load Balancing health check\. If an Elastic Load Balancing health check is not used, Auto Scaling can only act upon the health of the Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. Auto Scaling will not act on the application running on the instance\.

**Check ID**  
`CLOG40CDO8`

## Auto Scaling Group Resources<a name="auto-scaling-group-resources"></a>

**Description**  
Checks the availability of resources associated with launch configurations and your Auto Scaling groups\.   
Auto Scaling groups that point to unavailable resources cannot launch new Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. When properly configured, Auto Scaling causes the number of Amazon EC2 instances to increase seamlessly during demand spikes, and decrease automatically during demand lulls\. Auto Scaling groups and launch configurations that point to unavailable resources do not operate as intended\.

**Check ID**  
`8CNsSllI5v`

## AWS Direct Connect Connection Redundancy<a name="aws-direct-connect-connection-redundancy"></a>

**Description**  
Checks for AWS Regions that have only one AWS Direct Connect connection\. Connectivity to your AWS resources should have two Direct Connect connections configured at all times to provide redundancy in case a device is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`0t121N1Ty3`

## AWS Direct Connect Location Redundancy<a name="aws-direct-connect-location-redundancy"></a>

**Description**  
Checks for AWS Regions with one or more AWS Direct Connect connections and only one AWS Direct Connect location\. Connectivity to your AWS resources should have Direct Connect connections configured to different Direct Connect locations to provide redundancy in case a location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`8M012Ph3U5`

## AWS Direct Connect Virtual Interface Redundancy<a name="aws-direct-connect-virtual-interface-redundancy"></a>

**Description**  
Checks for virtual private gateways with AWS Direct Connect virtual interfaces \(VIFs\) that are not configured on at least two AWS Direct Connect connections\. Connectivity to your virtual private gateway should have multiple VIFs configured across multiple Direct Connect connections and locations\. This provides redundancy in case that a device or location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`4g3Nt5M1Th`

## AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy<a name="aws-lambda-vpc-enabled-functions-without-multi-az-redundancy"></a>

**Description**  
Checks for VPC\-enabled Lambda functions that are vulnerable to service interruption in a single Availability Zone\. It is recommended for VPC\-enabled functions to be connected to multiple Availability Zones for high availability\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q4C6`

## AWS Well\-Architected high risk issues for reliability<a name="well-architected-high-risk-issues-reliability"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the reliability pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L4`

## ELB Connection Draining<a name="elb-connection-draining"></a>

**Description**  
Checks for load balancers that do not have connection draining enabled\.   
When connection draining is not enabled and you deregister an Amazon EC2 instance from a load balancer, the load balancer stops routing traffic to that instance and closes the connection\. When connection draining is enabled, the load balancer stops sending new requests to the deregistered instance but keeps the connection open to serve active requests\.

**Check ID**  
`7qGXsKIUw`

## ELB Cross\-Zone Load Balancing<a name="elb-cross-zone-load-balancing"></a>

**Description**  
With cross\-zone load balancing turned off, there is a risk of service unavailability due to uneven distribution of traffic or backend overloading\. This problem can occur when clients incorrectly cache DNS information\. The problem can also occur when there are an unequal number of instances in each Availability Zone \(for example, if you have taken down some instances for maintenance\)\.

**Check ID**  
`xdeXZKIUy`

## Load Balancer Optimization<a name="load-balancer-optimization"></a>

**Description**  
Checks your load balancer configuration\.   
To help increase the level of fault tolerance in Amazon Elastic Compute Cloud \(Amazon EC2\) when using Elastic Load Balancing , we recommend running an equal number of instances across multiple Availability Zones in a Region\. A load balancer that is configured accrues charges, so this is a cost\-optimization check as well\.

**Check ID**  
`iqdCTZKCUp`

## VPN Tunnel Redundancy<a name="vpn-tunnel-redundancy"></a>

**Description**  
Checks the number of tunnels that are active for each of your VPNs\.  
A VPN should have two tunnels configured at all times\. This provides redundancy in case of outage or planned maintenance of the devices at the AWS endpoint\. For some hardware, only one tunnel is active at a time\. If a VPN has no active tunnels, charges for the VPN might still apply\. For more information, see [AWS Client VPN Administrator Guide](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/)\.

**Check ID**  
`S45wrEXrLz`