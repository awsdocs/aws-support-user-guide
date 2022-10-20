# AWS managed policies for AWS Support Plans<a name="managed-policies-aws-support-plans"></a>

AWS Support Plans has the following managed policies\.

**Contents**
+ [AWS managed policy: AWSSupportPlansFullAccess](#support-plan-full-access-managed-policy)
+ [AWS managed policy: AWSSupportPlansReadOnlyAccess](#support-plan-read-only-access-managed-policy)
+ [AWS Support Plans updates to AWS managed policies](#security-iam-awsmanpol-updates-support-plans)

## AWS managed policy: AWSSupportPlansFullAccess<a name="support-plan-full-access-managed-policy"></a>

AWS Support Plans uses the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSSupportPlansFullAccess$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSSupportPlansFullAccess$jsonEditor) AWS managed policy\. The IAM entity uses this policy to complete the following Support Plans actions for you:
+ View your support plan for your AWS account
+ View details about the status for a request to change your support plan
+ Change the support plan for your AWS account

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "supportplans:GetSupportPlan",
                "supportplans:GetSupportPlanUpdateStatus",
                "supportplans:StartSupportPlanUpdate"
            ],
            "Resource": "*"
        }
    ]
}
```

For a list of changes to the policies, see [AWS Support Plans updates to AWS managed policies](#security-iam-awsmanpol-updates-support-plans)\.

## AWS managed policy: AWSSupportPlansReadOnlyAccess<a name="support-plan-read-only-access-managed-policy"></a>

AWS Support Plans uses the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSSupportPlansReadOnlyAccess$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSSupportPlansReadOnlyAccess$jsonEditor) AWS managed policy\. The IAM entity uses this policy to complete the following read\-only Support Plans actions for you:
+ View your support plan for your AWS account
+ View details about the status for a request to change your support plan

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "supportplans:GetSupportPlan",
                "supportplans:GetSupportPlanUpdateStatus"
            ],
            "Resource": "*"
        }
    ]
}
```

For a list of changes to the policies, see [AWS Support Plans updates to AWS managed policies](#security-iam-awsmanpol-updates-support-plans)\.

## AWS Support Plans updates to AWS managed policies<a name="security-iam-awsmanpol-updates-support-plans"></a>



View details about updates to AWS managed policies for Support Plans since these services began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the [Document history](History.md) page\.



The following table describes important updates to the Support Plans managed policies since September 29, 2022\.


**AWS Support**  

| Change | Description | Date | 
| --- | --- | --- | 
|  Change log published  |  Change log for the Support Plans managed policies\.  | September 29, 2022 | 