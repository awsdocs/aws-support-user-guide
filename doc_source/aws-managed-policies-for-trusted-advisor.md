# AWS managed policies for AWS Trusted Advisor<a name="aws-managed-policies-for-trusted-advisor"></a>

Trusted Advisor has the following AWS managed policies\.

**Contents**
+ [AWS managed policy: AWSTrustedAdvisorPriorityFullAccess](#security-iam-support-TA-priority-full-access-policy)
+ [AWS managed policy: AWSTrustedAdvisorPriorityReadOnlyAccess](#security-iam-support-TA-priority-read-only-policy)
+ [AWS managed policy: AWSTrustedAdvisorServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy)
+ [AWS managed policy: AWSTrustedAdvisorReportingServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorReportingServiceRolePolicy)
+ [Trusted Advisor updates to AWS managed policies](#security-iam-awsmanpol-updates-trusted-advisor)

## AWS managed policy: AWSTrustedAdvisorPriorityFullAccess<a name="security-iam-support-TA-priority-full-access-policy"></a>

The [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSTrustedAdvisorPriorityFullAccess$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSTrustedAdvisorPriorityFullAccess$jsonEditor) policy grants full access to Trusted Advisor Priority\. This policy also allows the user to add Trusted Advisor as a trusted service with AWS Organizations and to specify the delegated administrator accounts for Trusted Advisor Priority\.

 **Permissions details** 

In the first statement, the policy includes the following permissions for `trustedadvisor`:
+ Describes your account and organization\.
+ Describes identified risks from Trusted Advisor Priority\. The permissions allow you to download and update the risk status\.
+ Describes your configurations for Trusted Advisor Priority email notifications\. The permissions allow you to configure the email notifications and disable them for your delegated administrators\.
+ Sets up Trusted Advisor so that your account can enable AWS Organizations\.

In the second statement, the policy includes the following permissions for `organizations`:
+ Describes your Trusted Advisor account and organization\. 
+ Lists the AWS services that you enabled to use Organizations\.

In the third statement, the policy includes the following permissions for `organizations`:
+ Lists the delegated administrators for Trusted Advisor Priority\.
+ Enables and disables trusted access with Organizations\.

In the fourth statement, the policy includes the following permissions for `iam`:
+ Creates the `AWSServiceRoleForTrustedAdvisorReporting` service\-linked role\.

In the fifth statement, the policy includes the following permissions for `organizations`:
+ Allows you to register and deregister delegated administrators for Trusted Advisor Priority\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "trustedadvisor:DescribeAccount*",
                "trustedadvisor:DescribeOrganization",
                "trustedadvisor:DescribeRisk*",
                "trustedadvisor:DownloadRisk",
                "trustedadvisor:UpdateRiskStatus",
                "trustedadvisor:DescribeNotificationConfigurations",
                "trustedadvisor:UpdateNotificationConfigurations",
                "trustedadvisor:DeleteNotificationConfigurationForDelegatedAdmin",
                "trustedadvisor:SetOrganizationAccess"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeAccount",
                "organizations:DescribeOrganization",
                "organizations:ListAWSServiceAccessForOrganization"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:ListDelegatedAdministrators",
                "organizations:EnableAWSServiceAccess",
                "organizations:DisableAWSServiceAccess"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "organizations:ServicePrincipal": [
                        "reporting.trustedadvisor.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "arn:aws:iam::*:role/aws-service-role/reporting.trustedadvisor.amazonaws.com/AWSServiceRoleForTrustedAdvisorReporting",
            "Condition": {
                "StringLike": {
                    "iam:AWSServiceName": "reporting.trustedadvisor.amazonaws.com"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:RegisterDelegatedAdministrator",
                "organizations:DeregisterDelegatedAdministrator"
            ],
            "Resource": "arn:aws:organizations::*:*",
            "Condition": {
                "StringEquals": {
                    "organizations:ServicePrincipal": [
                        "reporting.trustedadvisor.amazonaws.com"
                    ]
                }
            }
        }
    ]
}
```

## AWS managed policy: AWSTrustedAdvisorPriorityReadOnlyAccess<a name="security-iam-support-TA-priority-read-only-policy"></a>

The [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSTrustedAdvisorPriorityReadOnlyAccess$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSTrustedAdvisorPriorityReadOnlyAccess$jsonEditor) policy grants read\-only permissions to Trusted Advisor Priority, including permission to view the delegated administrator accounts\.

 **Permissions details** 

In the first statement, the policy includes the following permissions for `trustedadvisor`:
+ Describes your Trusted Advisor account and organization\.
+ Describes the identified risks from Trusted Advisor Priority and allows you to download them\.
+ Describes the configurations for Trusted Advisor Priority email notifications\.

In the second and third statement, the policy includes the following permissions for `organizations`:
+ Describes your organization with Organizations\.
+ Lists the AWS services that you enabled to use Organizations\.
+ Lists the delegated administrators for Trusted Advisor Priority

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "trustedadvisor:DescribeAccount*",
                "trustedadvisor:DescribeOrganization",
                "trustedadvisor:DescribeRisk*",
                "trustedadvisor:DownloadRisk",
                "trustedadvisor:DescribeNotificationConfigurations"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeOrganization",
                "organizations:ListAWSServiceAccessForOrganization"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:ListDelegatedAdministrators"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "organizations:ServicePrincipal": [
                        "reporting.trustedadvisor.amazonaws.com"
                    ]
                }
            }
        }
    ]
}
```

## AWS managed policy: AWSTrustedAdvisorServiceRolePolicy<a name="security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy"></a>

 

 

This policy is attached to the `AWSServiceRoleForTrustedAdvisor` service\-linked role\. It allows the service\-linked role to perform actions for you\. You can't attach the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorServiceRolePolicy$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSTrustedAdvisorServiceRolePolicy$jsonEditor) to your AWS Identity and Access Management \(IAM\) entities\. For more information, see [Using service\-linked roles for Trusted Advisor](using-service-linked-roles-ta.md)\.

 

This policy grants administrative permissions that allow the service\-linked role to access AWS services\. These permissions allow the checks for Trusted Advisor to evaluate your account\.

 

 **Permissions details** 

This policy includes the following permissions\.

 

 
+ `Auto Scaling` – Describes Amazon EC2 Auto Scaling account quotas and resources
+ `cloudformation` – Describes AWS CloudFormation \(CloudFormation\) account quotas and stacks
+ `cloudfront` – Describes Amazon CloudFront distributions
+ `cloudtrail` – Describes AWS CloudTrail \(CloudTrail\) trails
+ `dynamodb` – Describes Amazon DynamoDB account quotas and resources
+ `ec2` – Describes Amazon Elastic Compute Cloud \(Amazon EC2\) account quotas and resources
+ `elasticloadbalancing` – Describes Elastic Load Balancing \(ELB\) account quotas and resources
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

## Trusted Advisor updates to AWS managed policies<a name="security-iam-awsmanpol-updates-trusted-advisor"></a>

 

View details about updates to AWS managed policies for AWS Support and Trusted Advisor since these services began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the [Document history](History.md) page\.

 

 

 

The following table describes important updates to the Trusted Advisor managed policies since August 10, 2021\.


**Trusted Advisor**  

| Change | Description | Date | 
| --- | --- | --- | 
|   [AWSTrustedAdvisorPriorityFullAccess](#security-iam-support-TA-priority-full-access-policy) and [AWSTrustedAdvisorPriorityReadOnlyAccess](#security-iam-support-TA-priority-read-only-policy)  New AWS managed policies for the Trusted Advisor  |  Trusted Advisor added two new managed policies that you can use to control access to Trusted Advisor Priority\.  |  August 17, 2022  | 
|  [AWSTrustedAdvisorServiceRolePolicy](#security-iam-awsmanpol-AWSTrustedAdvisorServiceRolePolicy) – Update to an existing policy  |  Trusted Advisor added new actions to grant the `DescribeTargetGroups` and `GetAccountPublicAccessBlock` permissions\. The `DescribeTargetGroup` permission is required for the **Auto Scaling Group Health Check** to retrieve non\-Classic Load Balancers that are attached to an Auto Scaling group\. The `GetAccountPublicAccessBlock` permission is required for the **Amazon S3 Bucket Permissions** check to retrieve the block public access settings for an AWS account\.  | August 10, 2021 | 
|  Change log published  |  Change log for the Trusted Advisor managed policies\.  | August 10, 2021 | 