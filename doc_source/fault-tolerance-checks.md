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

**Alert Criteria**  
Yellow: The instances in an Aurora DB cluster have different accessibility \(a mix of public and private\)\.

**Recommended Action**  
Modify the `Publicly Accessible` setting of the instances in the DB cluster so that they are all either public or private\. For details, see the instructions for MySQL instances at [Modifying a DB Instance Running the MySQL Database Engine](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ModifyInstance.MySQL.html)\.

**Additional Resources**  
[Fault Tolerance for an Aurora DB Cluster](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Managing.html#Aurora.Managing.FaultTolerance)

**Report columns**  
+ Status
+ Region
+ Cluster
+ Public DB Instances
+ Private DB Instances
+ Reason

## Amazon Comprehend Endpoint Access Risk<a name="amazon-comprehend-endpoint-access-risk"></a>

**Description**  
Checks the AWS Key Management Service \(AWS KMS\) key permissions for an endpoint where the underlying model was encrypted by using customer managed keys\. If the customer managed key is disabled, or the key policy was changed to alter the allowed permissions for Amazon Comprehend, the endpoint availability might be affected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Cm24dfsM13`

**Alert Criteria**  
Red: The customer managed key is disabled or the key policy was changed to alter the allowed permissions for Amazon Comprehend access\.

**Recommended Action**  
If the customer managed key was disabled, we recommend that you enable it\. For more information, see [Enabling keys](https://docs.aws.amazon.com/kms/latest/developerguide/enabling-keys.html)\. If the key policy was altered and you want to keep using the endpoint, we recommend that you update the AWS KMS key policy\. For more information, see [Changing a key policy](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying.html)\.

**Additional Resources**  
[AWS KMS Key Encryption Permissions](https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions.html#auth-kms-permissions)

**Report columns**  
+ Status
+ Region
+ Endpoint ARN
+ Model ARN
+ KMS KeyId
+ Last Updated Time

## Amazon EBS Snapshots<a name="amazon-ebs-snapshots"></a>

**Description**  
Checks the age of the snapshots for your Amazon Elastic Block Store \(Amazon EBS\) volumes \(either available or in\-use\)\.   
Even though Amazon EBS volumes are replicated, failures can occur\. Snapshots are persisted to Amazon Simple Storage Service \(Amazon S3\) for durable storage and point\-in\-time recovery\.

**Check ID**  
`H7IgTzjTYb`

**Alert Criteria**  
+ Yellow: The most recent volume snapshot is between 7 and 30 days old\.
+ Red: The most recent volume snapshot is more than 30 days old\.
+ Red: The volume does not have a snapshot\.

**Recommended Action**  
 Create weekly or monthly snapshots of your volumes\. For more information, see [Creating an Amazon EBS Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-snapshot.html)\.

**Additional Resources**  
[Amazon Elastic Block Store \(Amazon EBS\)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)

**Report columns**  
+ Status
+ Region
+ Volume ID
+ Volume Name
+ Snapshot ID
+ Snapshot Name
+ Snapshot Age
+ Volume Attachment
+ Reason

## Amazon EC2 Availability Zone Balance<a name="amazon-ecs-availability-zone-balance"></a>

**Description**  
Checks the distribution of Amazon Elastic Compute Cloud \(Amazon EC2\) instances across Availability Zones in a Region\.   
Availability Zones are distinct locations that are insulated from failures in other Availability Zones\. This allows inexpensive, low\-latency network connectivity between Availability Zones in the same Region\. By launching instances in multiple Availability Zones in the same Region, you can help protect your applications from a single point of failure\.

**Check ID**  
`wuy7G1zxql`

**Alert Criteria**  
+  Yellow: The Region has instances in multiple zones, but the distribution is uneven \(the difference between the highest and lowest instance counts in utilized Availability Zones is greater than 20%\)\.
+  Red: The Region has instances only in a single Availability Zone\.

**Recommended Action**  
Balance your Amazon EC2 instances evenly across multiple Availability Zones\. You can do this by launching instances manually or by using Auto Scaling to do it automatically\. For more information, see [Launch Your Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/LaunchingAndUsingInstances.html) and [Load Balance Your Auto Scaling Group](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/US_SetUpASLBApp.html)\.

**Additional Resources**  
[Amazon EC2 Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/ec2/userguide/)

**Report columns**  
+ Status
+ Region
+ Zone a Instances
+ Zone b Instances
+ Zone c Instances
+ Zone e Instances
+ Zone f Instances
+ Reason

## Amazon RDS Backups<a name="amazon-rds-backups"></a>

**Description**  
Checks for automated backups of Amazon RDS DB instances\.   
By default, backups are enabled with a retention period of one day\. Backups reduce the risk of unexpected data loss and allow for point\-in\-time recovery\. 

**Check ID**  
`opQPADkZvH`

**Alert Criteria**  
Red: A DB instance has the backup retention period set to 0 days\.

**Recommended Action**  
Set the retention period for the automated DB instance backup to 1 to 35 days as appropriate to the requirements of your application\. See [Working With Automated Backups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)\.

**Additional Resources**  
[Getting Started with Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.html)

**Report columns**  
+ Status
+ Region/AZ
+ DB Instance
+ VPC ID
+ Backup Retention Period

## Amazon RDS Multi\-AZ<a name="amazon-rds-multi-az"></a>

**Description**  
Checks for DB instances that are deployed in a single Availability Zone \(AZ\)\.   
Multi\-AZ deployments enhance database availability by synchronously replicating to a standby instance in a different Availability Zone\. During planned database maintenance, or the failure of a DB instance or Availability Zone, Amazon RDS automatically fails over to the standby\. This failover allows database operations to resume quickly without administrative intervention\. Because Amazon RDS does not support Multi\-AZ deployment for Microsoft SQL Server, this check does not examine SQL Server instances\.

**Check ID**  
`f2iK5R6Dep`

**Alert Criteria**  
Yellow: A DB instance is deployed in a single Availability Zone\.

**Recommended Action**  
If your application requires high availability, modify your DB instance to enable Multi\-AZ deployment\. See [High Availability \(Multi\-AZ\)](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html)\.

**Additional Resources**  
[Regions and Availability Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html)

**Report columns**  
+ Status
+ Region/AZ
+ DB Instance
+ VPC ID
+ Multi\-AZ

## Amazon Route 53 Deleted Health Checks<a name="amazon-route-53-deleted-health-checks"></a>

**Description**  
Checks for resource record sets that are associated with health checks that have been deleted\.  
Route 53 does not prevent you from deleting a health check that is associated with one or more resource record sets\. If you delete a health check without updating the associated resource record sets, the routing of DNS queries for your DNS failover configuration will not work as intended\.   
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`Cb877eB72b`

**Alert Criteria**  
Yellow: A resource record set is associated with a health check that has been deleted\.

**Recommended Action**  
Create a new health check and associate it with the resource record set\. See [Creating, Updating, and Deleting Health Checks](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-creating-deleting.html) and [Adding Health Checks to Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-adding-to-rrsets.html)\. 

**Additional Resources**  
+ [Amazon Route 53 Health Checks and DNS Failover](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html)
+ [How Health Checks Work in Simple Amazon Route 53 Configurations](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-simple-configs.html)

**Report columns**  
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Resource Record Set Type
+ Resource Record Set Identifier

## Amazon Route 53 Failover Resource Record Sets<a name="amazon-route-53-failover-resource-record-sets"></a>

**Description**  
Checks for Amazon Route 53 failover resource record sets that have a misconfiguration\.   
When Amazon Route 53 health checks determine that the primary resource is unhealthy, Amazon Route 53 responds to queries with a secondary, backup resource record set\. You must create correctly configured primary and secondary resource record sets for failover to work\.   
Hosted zones created by AWS services won't appear in your check results\. 

**Check ID**  
`b73EEdD790`

**Alert Criteria**  
+ Yellow: A primary failover resource record set does not have a corresponding secondary resource record set\.
+ Yellow: A secondary failover resource record set does not have a corresponding primary resource record set\.
+ Yellow: Primary and secondary resource record sets that have the same name are associated with the same health check\. 

**Recommended Action**  
 If a failover resource set is missing, create the corresponding resource record set\. See [Creating Failover Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/creating-failover-rrsets.html)\.  
If your resource record sets are associated with the same health check, create separate health checks for each one\. See [Creating, Updating, and Deleting Health Checks](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-creating-deleting.html)\. 

**Additional Resources**  
[Amazon Route 53 Health Checks and DNS Failover](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html)

**Report columns**  
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Resource Record Set Type
+ Reason

## Amazon Route 53 High TTL Resource Record Sets<a name="amazon-route-53-high-ttl-resource-record-sets"></a>

**Description**  
Checks for resource record sets that can benefit from having a lower time\-to\-live \(TTL\) value\.   
TTL is the number of seconds that a resource record set is cached by DNS resolvers\. When you specify a long TTL, DNS resolvers take longer to request updated DNS records, which can cause unnecessary delay in rerouting traffic\. For example, a long TTL creates a delay between when DNS Failover detects an endpoint failure, and when it responds by rerouting traffic\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`C056F80cR3`

**Alert Criteria**  
+ Yellow: A resource record set whose routing policy is Failover has a TTL greater than 60 seconds\.
+ Yellow: A resource record set with an associated health check has a TTL greater than 60 seconds\.

**Recommended Action**  
Enter a TTL value of 60 seconds for the listed resource record sets\. For more information, see [Working with Resource Record Sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/rrsets-working-with.html)\.

**Additional Resources**  
[Amazon Route 53 Health Checks and DNS Failover](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html)

**Report columns**  
+ Status
+ Hosted Zone Name
+ Hosted Zone ID
+ Resource Record Set Name
+ Resource Record Set Type
+ Resource Record Set ID
+ TTL

## Amazon Route 53 Name Server Delegations<a name="amazon-route-53-name-server-delegations"></a>

**Description**  
Checks for Amazon Route 53 hosted zones for which your domain registrar or DNS is not using the correct Route 53 name servers\.   
When you create a hosted zone, Route 53 assigns a delegation set of four name servers\. The names of these servers are ns\-*\#\#\#*\.awsdns\-*\#\#*\.com, \.net, \.org, and \.co\.uk, where *\#\#\#* and *\#\#* typically represent different numbers\. Before Route 53 can route DNS queries for your domain, you must update your registrar's name server configuration to remove the name servers that the registrar assigned\. Then, you must add all four name servers in the Route 53 delegation set\. For maximum availability, you must add all four Route 53 name servers\.  
Hosted zones created by AWS services won't appear in your check results\.

**Check ID**  
`cF171Db240`

**Alert Criteria**  
Yellow: A hosted zone for which the registrar for your domain does not use all four of the Route 53 name servers in the delegation set\.

**Recommended Action**  
Add or update name server records with your registrar or with the current DNS service for your domain to include all four of the name servers in your Route 53 delegation set\. To find these values, see [Getting the Name Servers for a Hosted Zone](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/GetInfoAboutHostedZone.html)\. For information about adding or updating name server records, see [Creating and Migrating Domains and Subdomains to Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/creating-migrating.html)\.

**Additional Resources**  
[Working with Hosted Zones](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/AboutHZWorkingWith.html)

**Report columns**  
+ Hosted Zone Name
+ Hosted Zone ID
+ Number of Name Server Delegations Used

## Amazon S3 Bucket Logging<a name="amazon-s3-bucket-logging"></a>

**Description**  
Checks the logging configuration of Amazon Simple Storage Service \(Amazon S3\) buckets\.   
When server access logging is enabled, detailed access logs are delivered hourly to a bucket that you choose\. An access log record contains details about each request, such as the request type, the resources specified in the request, and the time and date the request was processed\. By default, bucket logging is not enabled\. You should enable logging if you want to perform security audits or learn more about users and usage patterns\.  
When logging is initially enabled, the configuration is automatically validated\. However, future modifications can result in logging failures\. This check examines explicit Amazon S3 bucket permissions, but it does not examine associated bucket policies that might override the bucket permissions\.

**Check ID**  
`BueAdJ7NrP`

**Alert Criteria**  
+ Yellow: The bucket does not have server access logging enabled\.
+ Yellow: The target bucket permissions do not include the root account, so Trusted Advisor cannot check it\.
+ Red: The target bucket does not exist\.
+ Red: The target bucket and the source bucket have different owners\.
+ Red: The log deliverer does not have write permissions for the target bucket\.

**Recommended Action**  
Enable bucket logging for most buckets\. See [Enabling Logging Using the Console](https://docs.aws.amazon.com/AmazonS3/latest/dev/enable-logging-console.html) and [Enabling Logging Programmatically](https://docs.aws.amazon.com/AmazonS3/latest/dev/enable-logging-programming.html)\.   
If the target bucket permissions do not include the root account and you want Trusted Advisor to check the logging status, add the root account as a grantee\. See [Editing Bucket Permissions](https://docs.aws.amazon.com/AmazonS3/latest/UG/EditingBucketPermissions.html)\.  
If the target bucket does not exist, select an existing bucket as a target or create a new one and select it\. See [Managing Bucket Logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html)\.  
If the target and source have different owners, change the target bucket to one that has the same owner as the source bucket\. See [Managing Bucket Logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html)\.  
If the log deliverer does not have write permissions for the target \(write not enabled\), grant Upload/Delete permissions to the Log Delivery group\. See [Editing Bucket Permissions](https://docs.aws.amazon.com/AmazonS3/latest/UG/EditingBucketPermissions.html)\. 

**Additional Resources**  
+ [Working with Buckets](https://docs.aws.amazon.com/AmazonS3/latest/UG/BucketOperations.html)
+ [Server Access Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html)
+ [Server Access Log Format](https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html)
+ [Deleting Log Files](https://docs.aws.amazon.com/AmazonS3/latest/dev/deleting-log-files-lifecycle.html)

**Report columns**  
+ Status
+ Region
+ Bucket Name
+ Target Name
+ Target Exists
+ Same Owner
+ Write Enabled
+ Reason

## Amazon S3 Bucket Versioning<a name="amazon-s3-bucket-versioning"></a>

**Description**  
Checks for Amazon Simple Storage Service buckets that do not have versioning enabled, or that have versioning suspended\.   
When versioning is enabled, you can easily recover from both unintended user actions and application failures\. Versioning allows you to preserve, retrieve, and restore any version of any object stored in a bucket\. You can use lifecycle rules to manage all versions of your objects, as well as their associated costs, by automatically archiving objects to the Glacier storage class\. Rules can also be configured to remove versions of your objects after a specified period of time\. You can also require multi\-factor authentication \(MFA\) for any object deletions or configuration changes to your buckets\.   
Versioning can't be deactivated after it has been enabled\. However, it can be suspended, which prevents new versions of objects from being created\. Using versioning can increase your costs for Amazon S3, because you pay for storage of multiple versions of an object\.

**Check ID**  
`R365s2Qddf`

**Alert Criteria**  
+ Green: Versioning is enabled for the bucket\.
+ Yellow: Versioning is not enabled for the bucket\.
+ Yellow: Versioning is suspended for the bucket\.

**Recommended Action**  
Enable bucket versioning on most buckets to prevent accidental deletion or overwriting\. See [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) and [Enabling Versioning Programmatically](https://docs.aws.amazon.com/AmazonS3/latest/dev/manage-versioning-examples.html)\.  
If bucket versioning is suspended, consider re\-enabling versioning\. For information on working with objects in a versioning\-suspended bucket, see [Managing Objects in a Versioning\-Suspended Bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/VersionSuspendedBehavior.html)\.  
When versioning is enabled or suspended, you can define lifecycle configuration rules to mark certain object versions as expired or to permanently remove unneeded object versions\. For more information, see [Object Lifecycle Management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html)\.  
MFA Delete requires additional authentication when the versioning status of the bucket is changed or when versions of an object are deleted\. It requires the user to enter credentials and a code from an approved authentication device\. For more information, see [MFA Delete](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html#MultiFactorAuthenticationDelete)\.

**Additional Resources**  
[Working with Buckets](https://docs.aws.amazon.com/AmazonS3/latest/UG/BucketOperations.html)

**Report columns**  
+ Status
+ Region
+ Bucket Name
+ Versioning
+ MFA Delete Enabled

## Auto Scaling Group Health Check<a name="auto-scaling-group-health-check"></a>

**Description**  
Examines the health check configuration for Auto Scaling groups\.   
If Elastic Load Balancing is being used for an Auto Scaling group, the recommended configuration is to enable an Elastic Load Balancing health check\. If an Elastic Load Balancing health check is not used, Auto Scaling can only act upon the health of the Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. Auto Scaling will not act on the application running on the instance\.

**Check ID**  
`CLOG40CDO8`

**Alert Criteria**  
+ Yellow: An Auto Scaling group has an associated load balancer, but the Elastic Load Balancing health check is not enabled\.
+ Yellow: An Auto Scaling group does not have an associated load balancer, but the Elastic Load Balancing health check is enabled\.

**Recommended Action**  
If the Auto Scaling group has an associated load balancer, but the Elastic Load Balancing health check is not enabled, see [Add an Elastic Load Balancing Health Check to your Auto Scaling Group](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/as-add-elb-healthcheck.html)\.  
If the Elastic Load Balancing health check is enabled, but no load balancer is associated with the Auto Scaling group, see [Set Up an Auto\-Scaled and Load\-Balanced Application](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/as-register-lbs-with-asg.html)\.

**Additional Resources**  
[Amazon EC2 Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/ec2/userguide/)

**Report columns**  
+ Status
+ Region
+ Auto Scaling Group Name
+ Load Balancer Associated
+ Health Check

## Auto Scaling Group Resources<a name="auto-scaling-group-resources"></a>

**Description**  
Checks the availability of resources associated with launch configurations and your Auto Scaling groups\.   
Auto Scaling groups that point to unavailable resources cannot launch new Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. When properly configured, Auto Scaling causes the number of Amazon EC2 instances to increase seamlessly during demand spikes, and decrease automatically during demand lulls\. Auto Scaling groups and launch configurations that point to unavailable resources do not operate as intended\.

**Check ID**  
`8CNsSllI5v`

**Alert Criteria**  
+ Red: An Auto Scaling group is associated with a deleted load balancer\.
+ Red: A launch configuration is associated with a deleted Amazon Machine Image \(AMI\)\.

**Recommended Action**  
If the load balancer has been deleted, either create a new load balancer and then create a new Auto Scaling group with the new load balancer, or create a new Auto Scaling group without the load balancer\. For information about creating a new Auto Scaling group with a new load balancer, see [Set Up an Auto\-Scaled and Load\-Balanced Application](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/as-register-lbs-with-asg.html)\. For information about creating a new Auto Scaling group without a load balancer, see Create Auto Scaling Group in [Getting Started With Auto Scaling Using the Console](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/USBasicSetup-Console.html)\.  
If the AMI has been deleted, create a new launch configuration using a valid AMI and associate it with an Auto Scaling group\. See Create Launch Configuration in [Getting Started With Auto Scaling Using the Console](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/USBasicSetup-Console.html)\.

**Additional Resources**  
+ [Troubleshooting Auto Scaling: Amazon EC2 AMIs](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/ts-as-ami.html)
+ [Troubleshooting Auto Scaling: Load Balancer Configuration](https://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/ts-as-loadbalancer.html)
+ [Amazon EC2 Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/latest/userguide/)

**Report columns**  
+ Status
+ Region
+ Auto Scaling Group Name
+ Launch Type
+ Resource Type
+ Resource Name

## AWS Direct Connect Connection Redundancy<a name="aws-direct-connect-connection-redundancy"></a>

**Description**  
Checks for AWS Regions that have only one AWS Direct Connect connection\. Connectivity to your AWS resources should have two Direct Connect connections configured at all times to provide redundancy in case a device is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`0t121N1Ty3`

**Alert Criteria**  
 Yellow: The AWS Region has only one AWS Direct Connect connection\.

**Recommended Action**  
 Configure an additional Direct Connect connection in this AWS Region to protect against device unavailability\. For more information, see [Configure Redundant Connections with AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html)\. To protect against site unavailability and add location redundancy, configure the additional Direct Connect connection to a different Direct Connect location\.

**Additional Resources**  
+ [Getting Started with AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html)
+ [AWS Direct Connect FAQs](http://aws.amazon.com/directconnect/faqs/)

**Report columns**  
+ Status
+ Region
+ Time Stamp
+ Location
+ Connection ID

## AWS Direct Connect Location Redundancy<a name="aws-direct-connect-location-redundancy"></a>

**Description**  
Checks for AWS Regions with one or more AWS Direct Connect connections and only one AWS Direct Connect location\. Connectivity to your AWS resources should have Direct Connect connections configured to different Direct Connect locations to provide redundancy in case a location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`8M012Ph3U5`

**Alert Criteria**  
Yellow: The Direct Connect connections in the AWS Region are not configured to different locations\.

**Recommended Action**  
 Configure a Direct Connect connection that uses a different Direct Connect location to protect against location unavailability\. For more information, see [Getting Started with AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html)\.

**Additional Resources**  
+ [Getting Started with AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html)
+ [AWS Direct Connect FAQs](http://aws.amazon.com/directconnect/faqs/)

**Report columns**  
+ Status
+ Region
+ Time Stamp
+ Location
+ Connection Details

## AWS Direct Connect Virtual Interface Redundancy<a name="aws-direct-connect-virtual-interface-redundancy"></a>

**Description**  
Checks for virtual private gateways with AWS Direct Connect virtual interfaces \(VIFs\) that are not configured on at least two AWS Direct Connect connections\. Connectivity to your virtual private gateway should have multiple VIFs configured across multiple Direct Connect connections and locations\. This provides redundancy in case that a device or location is unavailable\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\.

**Check ID**  
`4g3Nt5M1Th`

**Alert Criteria**  
Yellow: A virtual private gateway has less than two virtual interfaces, or the interfaces are not configured to multiple Direct Connect connections\. 

**Recommended Action**  
Configure at least two virtual interfaces that are configured to two Direct Connect connections to protect against device or location unavailability\. See [Create a Virtual Interface\.](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getstarted.html#createvirtualinterface)

**Additional Resources**  
+ [Getting Started with AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html)
+ [AWS Direct Connect FAQs](http://aws.amazon.com/directconnect/faqs/)
+ [Working With AWS Direct Connect Virtual Interfaces](https://docs.aws.amazon.com/directconnect/latest/UserGuide/WorkingWithVirtualInterfaces.html)

**Report columns**  
+ Status
+ Region
+ Time Stamp
+ Gateway ID
+ Location for VIF
+ Connection ID for VIF

## AWS Lambda VPC\-enabled Functions without Multi\-AZ Redundancy<a name="aws-lambda-vpc-enabled-functions-without-multi-az-redundancy"></a>

**Description**  
Checks for VPC\-enabled Lambda functions that are vulnerable to service interruption in a single Availability Zone\. It is recommended for VPC\-enabled functions to be connected to multiple Availability Zones for high availability\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`L4dfs2Q4C6`

**Alert Criteria**  
Yellow: A VPC\-enabled Lambda function connected to subnets in a single Availability Zone\.

**Recommended Action**  
When configuring functions for access to your VPC, choose subnets in multiple Availability Zones to ensure high availability\.

**Additional Resources**  
+ [Configuring a Lambda function to access resources in a VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html)
+ [Resilience in AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/security-resilience.html)

**Report columns**  
+ Status
+ Region
+ Function ARN
+ VPC ID
+ Average daily Invokes
+ Last Updated Time

## AWS Well\-Architected high risk issues for reliability<a name="well-architected-high-risk-issues-reliability"></a>

**Description**  
Checks for high risk issues \(HRIs\) for your workloads in the reliability pillar\. This check is based on your AWS\-Well Architected reviews\. Your check results depend on whether you completed the workload evaluation with AWS Well\-Architected\.  
Results for this check are automatically refreshed several times daily, and refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from this check\.

**Check ID**  
`Wxdfp4B1L4`

**Alert Criteria**  
+ Red: At least one active high risk issue was identified in the reliability pillar for AWS Well\-Architected\.
+ Green: No active high risk issues were detected in the reliability pillar for AWS Well\-Architected\.

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
+ Number of identified HRIs for Reliability
+ Number of HRIs resolved for Reliability
+ Number of questions answered for Reliability
+ Total number of questions in Reliability pillar
+ Last Updated Time

## ELB Connection Draining<a name="elb-connection-draining"></a>

**Description**  
Checks for load balancers that do not have connection draining enabled\.   
When connection draining is not enabled and you deregister an Amazon EC2 instance from a load balancer, the load balancer stops routing traffic to that instance and closes the connection\. When connection draining is enabled, the load balancer stops sending new requests to the deregistered instance but keeps the connection open to serve active requests\.

**Check ID**  
`7qGXsKIUw`

**Alert Criteria**  
Yellow: Connection draining is not enabled for a load balancer\.

**Recommended Action**  
Enable connection draining for the load balancer\. For more information, see [Connection Draining](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html#conn-drain) and [Enable or Disable Connection Draining for Your Load Balancer](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/config-conn-drain.html)\.

**Additional Resources**  
[Elastic Load Balancing Concepts](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html)

**Report columns**  
+ Status
+ Region
+ Load Balancer Name
+ Reason

## ELB Cross\-Zone Load Balancing<a name="elb-cross-zone-load-balancing"></a>

**Description**  
With cross\-zone load balancing turned off, there is a risk of service unavailability due to uneven distribution of traffic or backend overloading\. This problem can occur when clients incorrectly cache DNS information\. The problem can also occur when there are an unequal number of instances in each Availability Zone \(for example, if you have taken down some instances for maintenance\)\.

**Check ID**  
`xdeXZKIUy`

**Alert Criteria**  
Yellow: Cross\-zone load balancing is not enabled for a load balancer\.

**Recommended Action**  
Confirm that the Amazon EC2 instances registered with the load balancer are launched in multiple Availability Zones, and then enable cross\-zone load balancing for the load balancer\. For more information, see [Availability Zones and Regions](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html#AZ-Region) and [Enable or Disable Cross\-Zone Load Balancing for Your Load Balancer](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-crosszone-lb.html)\.

**Additional Resources**  
+ [Request Routing](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html#request-routing)
+ [Elastic Load Balancing Concepts](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html)

**Report columns**  
+ Status
+ Region
+ Load Balancer Name
+ Reason

## Load Balancer Optimization<a name="load-balancer-optimization"></a>

**Description**  
Checks your load balancer configuration\.   
To help increase the level of fault tolerance in Amazon Elastic Compute Cloud \(Amazon EC2\) when using Elastic Load Balancing , we recommend running an equal number of instances across multiple Availability Zones in a Region\. A load balancer that is configured accrues charges, so this is a cost\-optimization check as well\.

**Check ID**  
`iqdCTZKCUp`

**Alert Criteria**  
+ Yellow: A load balancer is enabled for a single Availability Zone\.
+ Yellow: A load balancer is enabled for an Availability Zone that has no active instances\.
+ Yellow: The Amazon EC2 instances that are registered with a load balancer are unevenly distributed across Availability Zones\. \(The difference between the highest and lowest instance counts in utilized Availability Zones is more than 1, and the difference is more than 20% of the highest count\.\)

**Recommended Action**  
Ensure that your load balancer points to active and healthy instances in at least two Availability Zones\. For more information, see [Add Availability Zone](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html#US_AddLBAvailabilityZone)\.  
If your load balancer is configured for an Availability Zone with no healthy instances, or if there is an imbalance of instances across the Availability Zones, determine if all the Availability Zones are necessary\. Omit any unnecessary Availability Zones and ensure there is a balanced distribution of instances across the remaining Availability Zones\. For more information, see [Remove Availability Zone](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html#US_ShrinkLBApp04)\.

**Additional Resources**  
+ [Availability Zones and Regions](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyConcepts.html#AZ-Region)
+ [Managing Load Balancers](https://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/UserScenarios.html)
+ [Best Practices in Evaluating Elastic Load Balancing](http://aws.amazon.com/articles/1636185810492479)

**Report columns**  
+ Status
+ Region
+ Load Balancer Name
+ \# of Zones
+ Zone a Instances
+ Zone b Instances
+ Zone c Instances
+ Zone d Instances
+ Zone e Instances
+ Zone f Instances
+ Reason

## VPN Tunnel Redundancy<a name="vpn-tunnel-redundancy"></a>

**Description**  
Checks the number of tunnels that are active for each of your VPNs\.  
A VPN should have two tunnels configured at all times\. This provides redundancy in case of outage or planned maintenance of the devices at the AWS endpoint\. For some hardware, only one tunnel is active at a time\. If a VPN has no active tunnels, charges for the VPN might still apply\. For more information, see [AWS Client VPN Administrator Guide](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/)\.

**Check ID**  
`S45wrEXrLz`

**Alert Criteria**  
+ Yellow: A VPN has one active tunnel \(this is normal for some hardware\)\.
+ Yellow: A VPN has no active tunnels\.

**Recommended Action**  
Be sure that two tunnels are configured for your VPN connection, and that both are active if your hardware supports it\. If you no longer need a VPN connection, you can delete it to avoid charges\. For more information, see [Your Customer Gateway](https://docs.aws.amazon.com/AmazonVPC/latest/NetworkAdminGuide/Introduction.html) or [Deleting a VPN connection](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_VPN.html#delete-vpn)\.

**Additional Resources**  
+ [AWS Site\-to\-Site VPN User Guide](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
+ [Adding a Hardware Virtual Private Gateway to Your VPC](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_VPN.html)

**Report columns**  
+ Status
+ Region
+ VPN ID
+ VPC
+ Virtual Private Gateway
+ Customer Gateway
+ Active Tunnels
+ Reason