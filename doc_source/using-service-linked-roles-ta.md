# Using Service\-Linked Roles for Trusted Advisor<a name="using-service-linked-roles-ta"></a>

AWS Trusted Advisor uses AWS Identity and Access Management \(IAM\) [ service\-linked roles](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to Trusted Advisor\. Service\-linked roles are predefined by Trusted Advisor and include all the permissions that the service requires to call other AWS services on your behalf\. Trusted Advisor uses this role to check your usage across AWS and provide recommendations for optimizing your AWS environment\. For example, Trusted Advisor analyzes your Amazon EC2 instance use to help you reduce cost, increase performance, tolerate failures, and improve security\. 

This role simplifies getting started with your AWS account because you don’t have to manually add the necessary permissions for Trusted Advisor\. Trusted Advisor defines the permissions of its service\-linked role, and only Trusted Advisor can assume this role\. The defined permissions include the trust policy and the permissions policy\. That permissions policy cannot be attached to any other IAM entity\.

You can delete the role only after first disabling Trusted Advisor\. This prevents you from removing permissions required by Trusted Advisor operations\. When you disable Trusted Advisor, you disable all service features, including offline processing and notifications\. Also, if you disable Trusted Advisor for a linked account, then the separate payer account will also be affected, negating some cost\-saving functionality\. You can re\-enable Trusted Advisor only after installing the AWSServiceRoleForTrustedAdvisor in the account via IAM\.

**Note**  
AWS Support uses a separate IAM service\-linked role for accessing your account’s resources to provide billing, administrative, and support services\. For more information, see [Using Service\-Linked Roles for AWS Support ](using-service-linked-roles-sup.md)\.

For information about other services that support service\-linked roles, see [AWS Services That Work with IAM](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-Linked Role Permissions for Trusted Advisor<a name="service-linked-role-permissions-ta"></a>

Trusted Advisor uses the service\-linked role named AWSServiceRoleForTrustedAdvisor — which allows Trusted Advisor to access AWS services on your behalf\.

The AWSServiceRoleForTrustedAdvisor service\-linked role trusts the following services to assume the role:
+ `trustedadvisor.amazonaws.com`

The role permissions policy allows Trusted Advisor to complete the following actions on the specified resources:
+ Action: `Read-only access` on `all AWS resources`

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\.

**To allow an IAM entity to create the AWSServiceRoleForTrustedAdvisor service\-linked role**

This is necessary only if the Trusted Advisor account is disabled, the service\-linked role is deleted, and the user must recreate the role to re\-enable Trusted Advisor\. 

Add the following statement to the permissions policy for the IAM entity that needs to create the service\-linked role:

```
{
    "Effect": "Allow",
    "Action": [
        "iam:CreateServiceLinkedRole",
        "iam:PutRolePolicy"
    ],
    "Resource": "arn:aws:iam::*:role/aws-service-role/trustedadvisor.amazonaws.com/AWSServiceRoleForTrustedAdvisor*",
    "Condition": {"StringLike": {"iam:AWSServiceName": "trustedadvisor.amazonaws.com"}}
}
```

**To allow an IAM entity to edit the description of the AWSServiceRoleForTrustedAdvisor service\-linked role**

Due to the nature of this role, only its description can be edited\.

Add the following statement to the permissions policy for the IAM entity that needs to edit the description of a service\-linked role:

```
{
    "Effect": "Allow",
    "Action": [
        "iam:UpdateRoleDescription"
    ],
    "Resource": "arn:aws:iam::*:role/aws-service-role/trustedadvisor.amazonaws.com/AWSServiceRoleForTrustedAdvisor*",
    "Condition": {"StringLike": {"iam:AWSServiceName": "trustedadvisor.amazonaws.com"}}
}
```

**To allow an IAM entity to delete the AWSServiceRoleForTrustedAdvisor service\-linked role**

Add the following statement to the permissions policy for the IAM entity that needs to delete a service\-linked role:

```
{
    "Effect": "Allow",
    "Action": [
        "iam:DeleteServiceLinkedRole",
        "iam:GetServiceLinkedRoleDeletionStatus"
    ],
    "Resource": "arn:aws:iam::*:role/aws-service-role/trustedadvisor.amazonaws.com/AWSServiceRoleForTrustedAdvisor*",
    "Condition": {"StringLike": {"iam:AWSServiceName": "trustedadvisor.amazonaws.com"}}
}
```

Alternatively, you can use an AWS managed policy, such as [AdministratorAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AdministratorAccess), to provide full access to Trusted Advisor\.

## Creating a Service\-Linked Role for Trusted Advisor<a name="create-service-linked-role-ta"></a>

You don't need to manually create the AWSServiceRoleForTrustedAdvisor service\-linked role\. When you open an AWS account, Trusted Advisor creates the service\-linked role for you\. 

**Important**  
If you were using the Trusted Advisor service before it began supporting service\-linked roles, then Trusted Advisor already created the AWSServiceRoleForTrustedAdvisor role in your account\. To learn more, see [A New Role Appeared in My IAM Account](http://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

If your account has no AWSServiceRoleForTrustedAdvisor service\-linked role, then Trusted Advisor will not work as expected\. This could happen if someone in your account disabled Trusted Advisor and then deleted the service\-linked role\. In this case, you can use IAM to create the "AWSServiceRoleForTrustedAdvisor" service\-linked role, and then enable Trusted Advisor\.

**To enable Trusted Advisor \(console\)**

1.  First, use the IAM console, the IAM CLI, or the IAM API to create a new service\-linked role using the Trusted Advisor use case\. For more information, see [Creating a Service\-Linked Role ](http://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) 

1. Sign in to the AWS Management Console and open the Trusted Advisor console at [https://console.aws.amazon.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor)\.

    Your Trusted Advisor console experience will be blocked by the **Disabled Trusted Advisor** status banner\. 

1. Choose **Enable Trusted Advisor Role** from the Disabled status banner\. Upon success, the Trusted Advisor console experience will be enabled\. If the required "AWSServiceRoleForTrustedAdvisor" is not detected, the Disabled status banner remains\.

## Editing a Service\-Linked Role for Trusted Advisor<a name="edit-service-linked-role-ta"></a>

Trusted Advisor does not allow you to edit the AWSServiceRoleForTrustedAdvisor service\-linked role if your account has no Trusted Advisor service\-linked role\. After you create a service\-linked role, you cannot change the name of the role, because various entities might reference the role\. However, you can use the IAM console, the IAM CLI, or the IAM API to edit the description of the role\. For more information, see [Editing a Service\-Linked Role](http://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a Service\-Linked Role for Trusted Advisor<a name="delete-service-linked-role-ta"></a>

If you no longer need to use any feature or service of Trusted Advisor, we recommend that you delete the AWSServiceRoleForTrustedAdvisor role\. Disabling Trusted Advisor and then deleting its service\-linked role will block all Trusted Advisor functionality for the entire account\. \(Note that some cost\-saving functionality within a separate, linked payer account will be negatively affected\.\) The Trusted Advisor console will be blocked, and will display the Disabled status; API calls to Trusted Advisor will return an Access Denied error\. Before you can delete the "AWSServiceRoleForTrustedAdvisor" using IAM, you must first disable Trusted Advisor in the console\.

### Cleaning Up a Service\-Linked Role<a name="service-linked-role-review-before-delete-ta"></a>

Before you can use IAM to delete a service\-linked role, you must first disable Trusted Advisor using the console\.

**To disable Trusted Advisor \(console\)**

1. Sign in to the AWS Management Console and open the Trusted Advisor console at [https://console.aws.amazon.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor)\.

1. In the navigation pane of the Trusted Advisor console, choose **Preferences**\.

1. In the **Service Linked Role Permissions** section, choose **Disable Trusted Advisor**\.

1. In the confirmation dialog box, confirm that you want to disable Trusted Advisor by choosing **OK**\.

When successful, all Trusted Advisor functionality is disabled, and the Trusted Advisor console displays only the Disabled status banner\. 

You can then use the IAM console, the IAM CLI, or the IAM API to delete the Trusted Advisor service\-linked role named "AWSServiceRoleForTrustedAdvisor\." For more information, see [Deleting a Service\-Linked Role ](http://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide *\. 