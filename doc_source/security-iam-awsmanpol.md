# AWS managed policies for AWS Support and AWS Trusted Advisor<a name="security-iam-awsmanpol"></a>







To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the `ViewOnlyAccess` AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

**Contents**
+ [AWS managed policy: AWSSupportServiceRolePolicy](#security-iam-awsmanpol-AWSSupportServiceRolePolicy)
+ [AWS managed policy: AWSTrustedAdvisorServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy)
+ [AWS managed policy: AWSTrustedAdvisorReportingServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorReportingServiceRolePolicy)
+ [AWS Support and Trusted Advisor updates to AWS managed policies](#security-iam-awsmanpol-updates)
+ [Permission changes for AWSSupportServiceRolePolicy](aws-support-service-link-role-updates.md)

## AWS managed policy: AWSSupportServiceRolePolicy<a name="security-iam-awsmanpol-AWSSupportServiceRolePolicy"></a>

AWS Support uses the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSSupportServiceRolePolicy$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSSupportServiceRolePolicy$jsonEditor) AWS managed policy\. This managed policy is attached to the `AWSServiceRoleForSupport` service\-linked role\. The policy allows the service\-linked role to complete actions on your behalf\. You can't attach this policy to your IAM entities\. For more information, see [Service\-linked role permissions for AWS Support](using-service-linked-roles-sup.md#service-linked-role-permissions)\.

For a list of changes to the policy, see [AWS Support and Trusted Advisor updates to AWS managed policies](#security-iam-awsmanpol-updates) and [Permission changes for AWSSupportServiceRolePolicy](aws-support-service-link-role-updates.md)\.









## AWS managed policy: AWSTrustedAdvisorServiceRolePolicy<a name="security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy"></a>





This policy is attached to the `AWSServiceRoleForTrustedAdvisor` service\-linked role\. It allows the service\-linked role to perform actions on your behalf\. You can't attach the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorServiceRolePolicy$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorServiceRolePolicy$jsonEditor) to your IAM entities\. For more information, see [Using service\-linked roles for Trusted Advisor](using-service-linked-roles-ta.md)\.



This policy grants administrative permissions that allow the service\-linked role to access AWS services\. These permissions allow the checks for Trusted Advisor to evaluate your account\.



**Permissions details**

This policy includes the following permissions\.




+ `Auto Scaling` – Describes Amazon EC2 Auto Scaling account quotas and resources
+ `cloudformation` – Describes AWS CloudFormation \(CloudFormation\) account quotas and stacks
+ `cloudfront` – Describes Amazon CloudFront distributions
+ `cloudtrail` – Describes AWS CloudTrail \(CloudTrail\) trails
+ `dynamodb` – Describes Amazon DynamoDB account quotas and resources
+ `ec2` – Describes Amazon Elastic Compute Cloud \(Amazon EC2\) account quotas and resources
+ `elasticloadbalancing` – Describes Elastic Load Balancing account quotas and resources
+ `iam` – Gets IAM resources, such as credentials, password policy, and certificates
+ `kinesis` – Describes Amazon Kinesis \(Kinesis\) account quotas
+ `rds` – Describes Amazon Relational Database Service \(Amazon RDS\) resources
+ `redshift` – Describes Amazon Redshift resources
+ `route53` – Describes Amazon Route 53 account quotas and resources
+ `s3` – Describes Amazon Simple Storage Service \(Amazon S3\) resources
+ `ses` – Gets Amazon Simple Email Service \(Amazon SES\) send quotas
+ `sqs` – Lists Amazon Simple Queue Service \(Amazon SQS\) queues
+ `cloudwatch` – Gets Amazon CloudWatch Events \(CloudWatch Events\) metric statistics
+ `ce` – Gets Cost Explorer Service \(Cost Explorer\) recommendations



```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "autoscaling:DescribeAccountLimits",
                "autoscaling:DescribeAutoScalingGroups",
                "autoscaling:DescribeLaunchConfigurations",
                "cloudformation:DescribeAccountLimits",
                "cloudformation:DescribeStacks",
                "cloudformation:ListStacks",
                "cloudfront:ListDistributions",
                "cloudtrail:DescribeTrails",
                "cloudtrail:GetTrailStatus",
                "dynamodb:DescribeLimits",
                "dynamodb:DescribeTable",
                "dynamodb:ListTables",
                "ec2:DescribeAddresses",
                "ec2:DescribeReservedInstances",
                "ec2:DescribeInstances",
                "ec2:DescribeVpcs",
                "ec2:DescribeInternetGateways",
                "ec2:DescribeImages",
                "ec2:DescribeVolumes",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeReservedInstancesOfferings",
                "ec2:DescribeSnapshots",
                "ec2:DescribeVpnConnections",
                "ec2:DescribeVpnGateways",
                "ec2:DescribeLaunchTemplateVersions",
                "elasticloadbalancing:DescribeAccountLimits",
                "elasticloadbalancing:DescribeInstanceHealth",
                "elasticloadbalancing:DescribeLoadBalancerAttributes",
                "elasticloadbalancing:DescribeLoadBalancerPolicies",
                "elasticloadbalancing:DescribeLoadBalancerPolicyTypes",
                "elasticloadbalancing:DescribeLoadBalancers",
                "elasticloadbalancing:DescribeTargetGroups",
                "iam:GenerateCredentialReport",
                "iam:GetAccountPasswordPolicy",
                "iam:GetAccountSummary",
                "iam:GetCredentialReport",
                "iam:GetServerCertificate",
                "iam:ListServerCertificates",
                "kinesis:DescribeLimits",
                "rds:DescribeAccountAttributes",
                "rds:DescribeDBClusters",
                "rds:DescribeDBEngineVersions",
                "rds:DescribeDBInstances",
                "rds:DescribeDBParameterGroups",
                "rds:DescribeDBParameters",
                "rds:DescribeDBSecurityGroups",
                "rds:DescribeDBSnapshots",
                "rds:DescribeDBSubnetGroups",
                "rds:DescribeEngineDefaultParameters",
                "rds:DescribeEvents",
                "rds:DescribeOptionGroupOptions",
                "rds:DescribeOptionGroups",
                "rds:DescribeOrderableDBInstanceOptions",
                "rds:DescribeReservedDBInstances",
                "rds:DescribeReservedDBInstancesOfferings",
                "rds:ListTagsForResource",
                "redshift:DescribeClusters",
                "redshift:DescribeReservedNodeOfferings",
                "redshift:DescribeReservedNodes",
                "route53:GetAccountLimit",
                "route53:GetHealthCheck",
                "route53:GetHostedZone",
                "route53:ListHealthChecks",
                "route53:ListHostedZones",
                "route53:ListHostedZonesByName",
                "route53:ListResourceRecordSets",
                "s3:GetAccountPublicAccessBlock",
                "s3:GetBucketAcl",
                "s3:GetBucketPolicy",
                "s3:GetBucketPolicyStatus",
                "s3:GetBucketLocation",
                "s3:GetBucketLogging",
                "s3:GetBucketVersioning",
                "s3:GetBucketPublicAccessBlock",
                "s3:ListBucket",
                "s3:ListAllMyBuckets",
                "ses:GetSendQuota",
                "sqs:ListQueues",
                "cloudwatch:GetMetricStatistics",
                "ce:GetReservationPurchaseRecommendation",
                "ce:GetSavingsPlansPurchaseRecommendation"
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSTrustedAdvisorReportingServiceRolePolicy<a name="security-iam-awsmanpol-AWSTrustedAdvisorReportingServiceRolePolicy"></a>





This policy is attached to the `AWSServiceRoleForTrustedAdvisorReporting` service\-linked role that allows Trusted Advisor to perform actions for the organizational view feature\. You can't attach the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorReportingServiceRolePolicy$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorReportingServiceRolePolicy$jsonEditor) to your IAM entities\. For more information, see [Using service\-linked roles for Trusted Advisor](using-service-linked-roles-ta.md)\.



This policy grants administrative permissions that allow the service\-linked role to perform AWS Organizations actions\.



**Permissions details**

This policy includes the following permissions\.




+ `organizations` – Describes your organization and lists the service access, accounts, parents, children, and organizational units



```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "organizations:DescribeOrganization",
                "organizations:ListAWSServiceAccessForOrganization",
                "organizations:ListAccounts",
                "organizations:ListAccountsForParent",
                "organizations:ListOrganizationalUnitsForParent",
                "organizations:ListChildren",
                "organizations:ListParents",
                "organizations:DescribeOrganizationalUnit",
                "organizations:DescribeAccount"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```





## AWS Support and Trusted Advisor updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>



View details about updates to AWS managed policies for AWS Support and Trusted Advisor since these services began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the [Document history](History.md) page\.



The following table describes important updates to the AWS Support managed policies since February 17, 2022\.


**AWS Support**  

| Change | Description | Date | 
| --- | --- | --- | 
|  [AWSSupportServiceRolePolicy](#security-iam-awsmanpol-AWSSupportServiceRolePolicy) – Update to an existing policy  |  Added 25 new permissions to the following services to perform actions that help troubleshoot customer issues related to billing, administrative, and technical support:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/awssupport/latest/user/security-iam-awsmanpol.html)  | April 27, 2022 | 
|  [AWSSupportServiceRolePolicy](#security-iam-awsmanpol-AWSSupportServiceRolePolicy) – Update to an existing policy  |  Added 54 new permissions to the following services to perform actions that help troubleshoot customer issues related to billing, administrative, and technical support:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/awssupport/latest/user/security-iam-awsmanpol.html)  | March 14, 2022 | 
|  [AWSSupportServiceRolePolicy](#security-iam-awsmanpol-AWSSupportServiceRolePolicy) – Update to an existing policy  |  Added 74 new permissions to the following services to perform actions that help troubleshoot customer issues related to billing, administrative, and technical support:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/awssupport/latest/user/security-iam-awsmanpol.html) For more information, see [Permission changes for AWSSupportServiceRolePolicy](aws-support-service-link-role-updates.md)\.  | February 17, 2022 | 
|  Change log published  |  Change log for the AWS Support managed policies\.  | February 17, 2022 | 

The following table describes important updates to the Trusted Advisor managed policies since August 10, 2021\.


**Trusted Advisor**  

| Change | Description | Date | 
| --- | --- | --- | 
|  [AWSTrustedAdvisorServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy) – Update to an existing policy  |  Trusted Advisor added new actions to grant the `DescribeTargetGroups` and `GetAccountPublicAccessBlock` permissions\. The `DescribeTargetGroup` permission is required for the **Auto Scaling Group Health Check** to retrieve non\-Classic Load Balancers that are attached to an Auto Scaling group\. The `GetAccountPublicAccessBlock` permission is required for the **Amazon S3 Bucket Permissions** check to retrieve the block public access settings for an AWS account\.  | August 10, 2021 | 
|  Change log published  |  Change log for the Trusted Advisor managed policies\.  | August 10, 2021 | 