# Using service\-linked roles for AWS Support<a name="using-service-linked-roles-sup"></a>

AWS Support tools gather information about your AWS resources through API calls to provide customer service and technical support\. To increase the transparency and auditability of support activities, AWS Support uses an AWS Identity and Access Management \(IAM\) [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. 

The `AWSServiceRoleForSupport` service\-linked role is a unique IAM role that is linked directly to AWS Support\. This service\-linked role is predefined, and it includes the permissions that AWS Support requires to call other AWS services on your behalf\.

The `AWSServiceRoleForSupport` service\-linked role trusts the `support.amazonaws.com` service to assume the role\. 

To provide these services, the role's predefined permissions give AWS Support access to resource metadata, not customer data\. Only AWS Support tools can assume this role, which exists within your AWS account\.

We redact fields that could contain customer data\. For example, the `Input` and `Output` fields of the [GetExecutionHistory](https://docs.aws.amazon.com/step-functions/latest/apireference/API_GetExecutionHistory.html) for the AWS Step Functions API call aren't visible to AWS Support\.  We use AWS KMS keys to encrypt sensitive fields\. These fields are redacted in the API response and aren't visible to AWS Support agents\.

**Note**  
AWS Trusted Advisor uses a separate IAM service\-linked role to access AWS resources for your account to provide best practice recommendations and checks\. For more information, see [Using service\-linked roles for Trusted Advisor](using-service-linked-roles-ta.md)\.

 The `AWSServiceRoleForSupport` service\-linked role enables all AWS Support API calls to be visible to customers through AWS CloudTrail\. This helps with monitoring and auditing requirements, because it provides a transparent way to understand the actions that AWS Support performs on your behalf\. For information about CloudTrail, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## Service\-linked role permissions for AWS Support<a name="service-linked-role-permissions"></a>

This role uses the `AWSSupportServiceRolePolicy` AWS managed policy\. This managed policy is attached to the role and allows the role permission to complete actions on your behalf\. 

These actions might include the following:
+  **Billing, administrative, support, and other customer services** – AWS customer service uses the permissions granted by the managed policy to perform a number of services as part of your support plan\. These include investigating and answering account and billing questions, providing administrative support for your account, increasing service quotas, and offering additional customer support\.
+  **Processing of service attributes and usage data for your AWS account** – AWS Support might use the permissions granted by the managed policy to access service attributes and usage data for your AWS account\. This policy allows AWS Support to provide billing, administrative, and technical support for your account\. Service attributes include your account’s resource identifiers, metadata tags, roles, and permissions\. Usage data includes usage policies, usage statistics, and analytics\.
+  **Maintaining the operational health of your account and its resources** – AWS Support uses automated tools to perform actions related to operational and technical support\.

For more information about the allowed services and actions, see the [https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSSupportServiceRolePolicy$jsonEditor](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSSupportServiceRolePolicy$jsonEditor) policy in the IAM console\.

**Note**  
AWS Support automatically updates the `AWSSupportServiceRolePolicy` policy once per month to add permissions for new AWS services and actions\.

For more information, see [AWS managed policies for AWS Support](security-iam-awsmanpol.md)\.

## Creating a service\-linked role for AWS Support<a name="create-service-linked-role"></a>

You don't need to manually create the `AWSServiceRoleForSupport` role\. When you create an AWS account, this role is automatically created and configured for you\.

**Important**  
If you used AWS Support before it began supporting service\-linked roles, then AWS created the `AWSServiceRoleForSupport` role in your account\. For more information, see [A new role appeared in my IAM account](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

## Editing and deleting a service\-linked role for AWS Support<a name="edit-service-linked-role"></a>

You can use IAM to edit the description for the `AWSServiceRoleForSupport` service\-linked role\. For more information, see [Editing a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

The `AWSServiceRoleForSupport` role is necessary for AWS Support to provide administrative, operational, and technical support for your account\. As a result, this role can't be deleted through the IAM console, API, or AWS Command Line Interface \(AWS CLI\)\. This protects your AWS account, because you can't inadvertently remove necessary permissions for administering support services\.

For more information about the `AWSServiceRoleForSupport` role or its uses, contact [AWS Support](http://aws.amazon.com/support)\.