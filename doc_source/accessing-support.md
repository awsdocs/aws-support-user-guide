# Access AWS Support<a name="accessing-support"></a>

You must have permissions to access Support Center and to [create a support case](case-management.md#creating-a-support-case)\.

You can use one of the following options to access Support Center:
+ Use the email address and password associated with your AWS account\. This identity is called the AWS account *root user*\.
+ Use AWS Identity and Access Management \(IAM\)\. 

If you have a Business or Enterprise Support plan, you can also use the [AWS Support API](Welcome.md) to access AWS Support and Trusted Advisor operations programmatically\. For more information, see the [AWS Support API Reference](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html)\.



**Note**  
If you can't sign in to Support Center, you can use the [Contact Us](http://aws.amazon.com/contact-us/) page instead\. You can use this page to get help with billing and account issues\.

## AWS account<a name="root-account"></a>

 You can sign in to the AWS Management Console and access the Support Center by using your AWS account email address and password\. This identity is called the AWS account *root user*\. However, we strongly recommend that you don't use the root user for your everyday tasks, even the administrative ones\. Instead, we recommend that you use IAM, which lets you control who can perform certain tasks in your account\. 

## IAM<a name="iam"></a>

By default, IAM users can't access the Support Center\. You can use IAM to create individual users or groups\. Then, you attach IAM policies to these entities, so that they have permission to perform actions and access resources, such as to open Support Center cases and use the AWS Support API\.

After you create IAM users, you can give those users individual passwords and an account\-specific sign\-in page\. They can then sign in to your AWS account and work in the Support Center\. IAM users who have AWS Support access can see all cases that are created for the account\. 

For more information, see [How IAM users sign in to your AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/WhatUsersNeedToKnow.html) in the *IAM User Guide*\.

The easiest way to grant permissions is to attach the AWS managed policy [AWSSupportAccess](https://console.aws.amazon.com/iam/home?region=us-east-1#/policies/arn:aws:iam::aws:policy/AWSSupportAccess) to the user, group, or role\. AWS Support allows action\-level permissions to control access to specific AWS Support operations\. AWS Support doesn't provide resource\-level access, so the `Resource` element is always set to `*`\. You can't allow or deny access to specific support cases\. 

**Example : Allow access to all AWS Support actions**  
The AWS managed policy [AWSSupportAccess](https://console.aws.amazon.com/iam/home?region=us-east-1#/policies/arn:aws:iam::aws:policy/AWSSupportAccess) grants an IAM user access to AWS Support\. An IAM user with this policy can access all AWS Support operations and resources\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["support:*"],
            "Resource": "*"
        }
    ]
}
```
For more information about how to attach the `AWSSupportAccess` policy to your entities, see [Adding IAM identity permissions \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html#add-policies-console) in the *IAM User Guide*\.

**Example : Allow access to all actions except the ResolveCase action**  
You can also create *customer managed policies* in IAM to specify what actions to allow or deny\. The following policy statement allows an IAM user to perform all actions in AWS Support except resolve a case\.  

```
{
   "Version": "2012-10-17",
   "Statement": [
   {
      "Effect": "Allow",
      "Action": "support:*",
      "Resource": "*"
   },
   {
       "Effect": "Deny",
       "Action": "support:ResolveCase",
       "Resource": "*"
    }]
}
```
For more information about how to create a customer managed IAM policy, see [Creating IAM policies \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) in the *IAM User Guide*\.

If the user or group already has a policy, you can add the AWS Support\-specific policy statement to that policy\. 

**Important**  
If you can't view cases in the Support Center, make sure that you have the required permissions\. You might need to contact your IAM administrator\. For more information, see [Identity and access management for AWS Support](security-iam.md)\.

## Access to AWS Trusted Advisor<a name="access-to-trusted-advisor"></a>

In the AWS Management Console, a separate `trustedadvisor` IAM namespace controls access to Trusted Advisor\. In the AWS Support API, the `support` IAM namespace controls access to Trusted Advisor\. For more information, see [Manage access for AWS Trusted Advisor](security-trusted-advisor.md)\.