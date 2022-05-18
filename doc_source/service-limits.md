# Service limits<a name="service-limits"></a>

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
+ [Route 53 Hosted Zones](#route-53-hosted-zones)
+ [Route 53 Max Health Checks](#route-53-max-health-checks)
+ [Route 53 Reusable Delegation Sets](#route-53-reusable-delegation-sets)
+ [Route 53 Traffic Policies](#route-53-traffic-policies)
+ [Route 53 Traffic Policy Instances](#route-53-traffic-policy-instances)
+ [SES Daily Sending Quota](#ses-daily-sending-quota)
+ [VPC](#vpc-quota-check)
+ [VPC Internet Gateways](#vpc-internet-gateways)

## Auto Scaling Groups<a name="auto-scaling-groups"></a>

**Description**  
Checks for usage that is more than 80% of the Auto Scaling Groups quota\.

**Check ID**  
`fW7HH0l7J9`

## Auto Scaling Launch Configurations<a name="auto-scaling-launch-configurations"></a>

**Description**  
Checks for usage that is more than 80% of the Auto Scaling launch configurations quota\.

**Check ID**  
`aW7HH0l7J9`

## CloudFormation Stacks<a name="cloudformation-stacks"></a>

**Description**  
Checks for usage that is more than 80% of the CloudFormation stacks quota\.

**Check ID**  
`gW7HH0l7J9`

## DynamoDB Read Capacity<a name="dynamo-db-read-capacity"></a>

**Description**  
Checks for usage that is more than 80% of the DynamoDB provisioned throughput limit for reads per AWS account\.

**Check ID**  
`6gtQddfEw6`

## DynamoDB Write Capacity<a name="dynamo-db-write-capacity"></a>

**Description**  
Checks for usage that is more than 80% of the DynamoDB provisioned throughput limit for writes per AWS account\.

**Check ID**  
`c5ftjdfkMr`

## EBS Active Snapshots<a name="ebs-active-snapshots"></a>

**Description**  
Checks for usage that is more than 80% of the EBS active snapshots quota\.

**Check ID**  
`eI7KK0l7J9`

## EBS Cold HDD \(sc1\) Volume Storage<a name="ebs-cold-hdd-sc1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Cold HDD \(sc1\) volume storage quota\.

**Check ID**  
`gH5CC0e3J9`

## EBS General Purpose SSD \(gp2\) Volume Storage<a name="ebs-general-purpose-ssd-gp2-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS General Purpose SSD \(gp2\) volume storage quota\.

**Check ID**  
`dH7RR0l6J9`

## EBS General Purpose SSD \(gp3\) Volume Storage<a name="ebs-general-purpose-ssd-gp3-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS General Purpose SSD \(gp3\) volume storage quota\.

**Check ID**  
`dH7RR0l6J3`

## EBS Magnetic \(standard\) Volume Storage<a name="ebs-magnetic-standard-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Magnetic \(standard\) volume storage quota\.

**Check ID**  
`cG7HH0l7J9`

## EBS Provisioned IOPS \(SSD\) Volume Aggregate IOPS<a name="ebs-provisioned-iops-ssd-volume-aggregate-iops"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS \(SSD\) volume aggregate IOPS quota\.

**Check ID**  
`tV7YY0l7J9`

## EBS Provisioned IOPS SSD \(io1\) Volume Storage<a name="ebs-provisioned-iops-ssd-io1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS SSD \(io1\) volume storage quota\.

**Check ID**  
`gI7MM0l7J9`

## EBS Provisioned IOPS SSD \(io2\) Volume Storage<a name="ebs-provisioned-iops-ssd-io2-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Provisioned IOPS SSD \(io2\) volume storage quota\.

**Check ID**  
`gI7MM0l7J2`

## EBS Throughput Optimized HDD \(st1\) Volume Storage<a name="ebs-throughput-optimized-hdd-st1-volume-storage"></a>

**Description**  
Checks for usage that is more than 80% of the EBS Throughput Optimized HDD \(st1\) volume storage quota\.

**Check ID**  
`wH7DD0l3J9`

## EC2 On\-Demand Instances<a name="ec2-on-demand-instances"></a>

**Description**  
Checks for usage that is more than 80% of the EC2 On\-Demand Instances quota\.

**Check ID**  
`0Xc6LMYG8P`

## EC2 Reserved Instance Leases<a name="ec2-reserved-instance-leases"></a>

**Description**  
Checks for usage that is more than 80% of the EC2 Reserved Instance leases quota\.

**Check ID**  
`iH7PP0l7J9`

## EC2\-Classic Elastic IP Addresses<a name="ec2-elastic-ip-addresses"></a>

**Description**  
Checks for usage that is more than 80% of the EC2\-Classic Elastic IP addresses quota\.

**Check ID**  
`aW9HH0l8J6`

## EC2\-VPC Elastic IP Address<a name="ec2-vpc-elastic-ip-address"></a>

**Description**  
Checks for usage that is more than 80% of the EC2\-VPC Elastic IP address quota\.

**Check ID**  
`lN7RR0l7J9`

## ELB Application Load Balancers<a name="elb-application-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Application Load Balancers quota\.

**Check ID**  
`EM8b3yLRTr`

## ELB Classic Load Balancers<a name="elb-classic-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Classic Load Balancers quota\.

**Check ID**  
`iK7OO0l7J9`

## ELB Network Load Balancers<a name="elb-network-load-balancers"></a>

**Description**  
Checks for usage that is more than 80% of the ELB Network Load Balancers quota\.

**Check ID**  
`8wIqYSt25K`

## IAM Group<a name="iam-group"></a>

**Description**  
Checks for usage that is more than 80% of the IAM group quota\.

**Check ID**  
`sU7XX0l7J9`

## IAM Instance Profiles<a name="iam-instance-profiles"></a>

**Description**  
Checks for usage that is more than 80% of the IAM instance profiles quota\.

**Check ID**  
`nO7SS0l7J9`

## IAM Policies<a name="iam-policies"></a>

**Description**  
Checks for usage that is more than 80% of the IAM policies quota\.

**Check ID**  
`pR7UU0l7J9`

## IAM Roles<a name="iam-roles"></a>

**Description**  
Checks for usage that is more than 80% of the IAM roles quota\.

**Check ID**  
`oQ7TT0l7J9`

## IAM Server Certificates<a name="iam-server-certificates"></a>

**Description**  
Checks for usage that is more than 80% of the IAM server certificates quota\.

**Check ID**  
`rT7WW0l7J9`

## IAM Users<a name="iam-users"></a>

**Description**  
Checks for usage that is more than 80% of the IAM users quota\.

**Check ID**  
`qS7VV0l7J9`

## Kinesis Shards per Region<a name="kinesis-shards-per-region"></a>

**Description**  
Checks for usage that is more than 80% of the Kinesis shards per Region quota\.

**Check ID**  
`bW7HH0l7J9`

## RDS Cluster Parameter Groups<a name="rds-cluster-parameter-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS cluster parameter groups quota\.

**Check ID**  
`jtlIMO3qZM`

## RDS Cluster Roles<a name="rds-cluster-roles"></a>

**Description**  
Checks for usage that is more than 80% of the RDS cluster roles quota\.

**Check ID**  
`7fuccf1Mx7`

## RDS Clusters<a name="rds-clusters"></a>

**Description**  
Checks for usage that is more than 80% of the RDS clusters quota\.

**Check ID**  
`gjqMBn6pjz`

## RDS DB Instances<a name="rds-db-instances"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB instances quota\.

**Check ID**  
`XG0aXHpIEt`

## RDS DB Manual Snapshots<a name="rds-db-manual-snapshots"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB manual snapshots quota\.

**Check ID**  
`dV84wpqRUs`

## RDS DB Parameter Groups<a name="rds-db-parameter-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB parameter groups quota\.

**Check ID**  
`jEECYg2YVU`

## RDS DB Security Groups<a name="rds-db-security-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS DB security groups quota\.

**Check ID**  
`gfZAn3W7wl`

## RDS Event Subscriptions<a name="rds-event-subscriptions"></a>

**Description**  
Checks for usage that is more than 80% of the RDS event subscriptions quota\.

**Check ID**  
`keAhfbH5yb`

## RDS Max Auths per Security Group<a name="rds-max-auths-per-security-group"></a>

**Description**  
Checks for usage that is more than 80% of the RDS max auths per security group quota\.

**Check ID**  
`dBkuNCvqn5`

## RDS Option Groups<a name="rds-option-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS option groups quota\.

**Check ID**  
`3Njm0DJQO9`

## RDS Read Replicas per Master<a name="rds-read-replicas-per-master"></a>

**Description**  
Checks for usage that is more than 80% of the RDS read replicas per master quota\.

**Check ID**  
`pYW8UkYz2w`

## RDS Reserved Instances<a name="rds-reserved-instances"></a>

**Description**  
Checks for usage that is more than 80% of the RDS Reserved Instances quota\.

**Check ID**  
`UUDvOa5r34`

## RDS Subnet Groups<a name="rds-subnet-groups"></a>

**Description**  
Checks for usage that is more than 80% of the RDS subnet groups quota\.

**Check ID**  
`dYWBaXaaMM`

## RDS Subnets per Subnet Group<a name="rds-subnets-per-subnet-group"></a>

**Description**  
Checks for usage that is more than 80% of the RDS subnets per subnet group quota\.

**Check ID**  
`jEhCtdJKOY`

## RDS Total Storage Quota<a name="rds-total-storage-quota"></a>

**Description**  
Checks for usage that is more than 80% of the RDS total storage quota\.

**Check ID**  
`P1jhKWEmLa`

## Route 53 Hosted Zones<a name="route-53-hosted-zones"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 hosted zones quota per account\.

**Check ID**  
`dx3xfcdfMr`

## Route 53 Max Health Checks<a name="route-53-max-health-checks"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 health checks quota per account\.

**Check ID**  
`ru4xfcdfMr`

## Route 53 Reusable Delegation Sets<a name="route-53-reusable-delegation-sets"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 reusable delegation sets quota per account\.

**Check ID**  
`ty3xfcdfMr`

## Route 53 Traffic Policies<a name="route-53-traffic-policies"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 traffic policies quota per account\.

**Check ID**  
`dx3xfbjfMr`

## Route 53 Traffic Policy Instances<a name="route-53-traffic-policy-instances"></a>

**Description**  
Checks for usage that is more than 80% of the Route 53 traffic policy instances quota per account\.

**Check ID**  
`dx8afcdfMr`

## SES Daily Sending Quota<a name="ses-daily-sending-quota"></a>

**Description**  
Checks for usage that is more than 80% of the Amazon SES daily sending quota\.

**Check ID**  
`hJ7NN0l7J9`

## VPC<a name="vpc-quota-check"></a>

**Description**  
Checks for usage that is more than 80% of the VPC quota\.

**Check ID**  
`jL7PP0l7J9`

## VPC Internet Gateways<a name="vpc-internet-gateways"></a>

**Description**  
Checks for usage that is more than 80% of the VPC Internet gateways quota\.

**Check ID**  
`kM7QQ0l7J9`