# Using Service\-Linked Roles for AWS Support<a name="using-service-linked-roles-sup"></a>

AWS Support tools gather information about your AWS resources through API calls to provide world\-class customer service and technical support\. In order to increase the transparency and auditability of support activities, AWS Support now uses an AWS Identity and Access Management \(IAM\) [service\-linked role ](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. The AWSServiceRoleForSupport service\-linked role is a unique IAM role that is linked directly to AWS Support\. This service\-linked role is predefined and includes all the permissions that AWS Support requires to call other AWS services on your behalf\. AWS Support uses this service\-linked role in a number of ways: 
+  **Billing, administrative, support, and other customer services\. ** As an AWS customer, you automatically have around\-the\-clock access to AWS customer service\. AWS customer service uses the permissions granted by the service\-linked role to perform a number of services as part of your support plan\. These include investigating and answering account and billing questions, providing administrative support for your account, increasing service limits, and offering additional customer support\. 
+  **Processing of service attributes and usage data for your AWS account\. ** To provide billing, administrative, and support services, AWS Support might use the permissions granted by the service\-linked role to access service attributes and usage data for your AWS account\. Service attributes include your account’s resource identifiers, metadata tags, roles, and permissions\. Usage data includes usage policies, usage statistics, and analytics\. 
+  **Maintaining the operational health of your account and its resources\. ** AWS Support uses automated tools to perform actions related to operational and technical support\. 

To provide these services, the role's predefined permissions give AWS Support access to resource metadata, not customer data\. Only AWS Support tools can assume this role, which exists within your AWS account\. 

For more information about the AWSServiceRoleForSupport role or its uses, contact [AWS Support ](http://aws.amazon.com/support)\. 

**Note**  
AWS Trusted Advisor uses a separate IAM service\-linked role for accessing your account’s AWS resources to provide best practice recommendations and checks\. For more information, see [Using Service\-Linked Roles for Trusted Advisor](using-service-linked-roles-ta.md)\. 

 The AWSServiceRoleForSupport service\-linked role enables all support API calls to be visible to customers through AWS CloudTrail\. This helps with monitoring and auditing requirements by providing a transparent way to understand the actions that AWS Support performs on your behalf\. For information about CloudTrail, see the [AWS CloudTrail User Guide](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\. 

## Service\-Linked Role Permissions for AWS Support<a name="service-linked-role-permissions"></a>

The AWSServiceRoleForSupport service\-linked role trusts the support\.amazonaws\.com service to assume the role\. The permissions policy of the service\-linked role contains all the permissions that AWS Support needs to complete actions on your behalf\. 

For more information about the AWSServiceRoleForSupport role or its uses, contact [AWS Support ](https://aws.amazon.com/support)\. 

## Creating a Service\-Linked Role for AWS Support<a name="create-service-linked-role"></a>

You don't need to manually create the AWSServiceRoleForSupport role\. When you create a new AWS account, this role is automatically created and configured for you\. 

**Important**  
If you were using AWS Support before it began supporting service\-linked roles, then AWS created the AWSServiceRoleForSupport role in your account\. To learn more, see [A New Role Appeared in My IAM Account ](http://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\. 

## Editing and Deleting a Service\-Linked Role for AWS Support<a name="edit-service-linked-role"></a>

You can use IAM to edit the description for the AWSServiceRoleForSupport service\-linked role\. For more information, see [Editing a Service\-Linked Role ](http://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide *\. 

The AWSServiceRoleForSupport role is necessary for AWS Support to provide administrative, operational, and technical support for your account\. As a result, this role cannot be deleted through the IAM console, API, or CLI\. This protects your AWS account because you can't inadvertently remove necessary permissions for administering support services\. 

For more information about the AWSServiceRoleForSupport role or its uses, contact [AWS Support ](http://aws.amazon.com/support)\. 