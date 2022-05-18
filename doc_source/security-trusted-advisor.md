# Manage access for AWS Trusted Advisor<a name="security-trusted-advisor"></a>

You can access AWS Trusted Advisor from the AWS Management Console\. All AWS accounts have access to a select core [Trusted Advisor checks](http://aws.amazon.com/premiumsupport/faqs/#TaFree)\. If you have a Business, Enterprise On\-Ramp, or Enterprise Support plan, you can access all checks\. for more information, see [AWS Trusted Advisor check reference](trusted-advisor-check-reference.md)\.

You can use AWS Identity and Access Management \(IAM\) to control access to Trusted Advisor\. 

**Topics**
+ [Permissions for the Trusted Advisor console](#using-the-trusted-advisor-console)
+ [Trusted Advisor actions](#trusted-advisor-operations)
+ [IAM policy examples](#iam-policy-examples-trusted-advisor)
+ [See also](#see-also-security-trusted-advisor)

## Permissions for the Trusted Advisor console<a name="using-the-trusted-advisor-console"></a>

To access the Trusted Advisor console, a user must have a minimum set of permissions\. These permissions must allow the user to list and view details about the Trusted Advisor resources in your AWS account\.

You can use the following options to control access to Trusted Advisor:
+ Use the Trusted Advisor console's tag filter feature\. The user or role must have permissions associated with the tags\. 

  You can use AWS managed policies or custom policies to assign permissions by tags\. For more information, see [Controlling access to and for IAM users and roles using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_iam-tags.html)\.
+ Create an IAM policy with the `trustedadvisor` namespace\. You can use this policy to specify permissions for actions and resources\.

When you create a policy, you can specify the namespace of the service to allow or deny an action\. The namespace for Trusted Advisor is `trustedadvisor`\. However, you can't use the `trustedadvisor` namespace to allow or deny Trusted Advisor API operations in the AWS Support API\. You must use the `support` namespace for AWS Support instead\.

**Note**  
If you have permissions to the [AWS Support](https://docs.aws.amazon.com/awssupport/latest/APIReference/) API, the Trusted Advisor widget in the AWS Management Console will show a summary view of your Trusted Advisor results\. To view your results in the Trusted Advisor console, you must have permission to the `trustedadvisor` namespace\.

## Trusted Advisor actions<a name="trusted-advisor-operations"></a>

You can perform the following Trusted Advisor actions in the console\. You can also specify these Trusted Advisor actions in an IAM policy to allow or deny specific actions\. 


| Action | Description | 
| --- | --- | 
|  `DescribeAccount`  |  Grants permission to view the AWS Support plan and various Trusted Advisor preferences\.  | 
|  `DescribeAccountAccess`  |  Grants permission to view if the AWS account has enabled or disabled Trusted Advisor\.  | 
|  `DescribeCheckItems`  |  Grants permission to view details for the check items\.  | 
|  `DescribeCheckRefreshStatuses`  |  Grants permission to view the refresh statuses for Trusted Advisor checks\.  | 
|  `DescribeCheckSummaries`  |  Grants permission to view Trusted Advisor check summaries\.  | 
|  `DescribeChecks`  |  Grants permission to view details for Trusted Advisor checks\.  | 
|   `DescribeNotificationPreferences`   |  Grants permission to view the notification preferences for the AWS account\.  | 
|   `ExcludeCheckItems`   |  Grants permission to exclude recommendations for Trusted Advisor checks\.  | 
|   `IncludeCheckItems`   |  Grants permission to include recommendations for Trusted Advisor checks\.  | 
|  `RefreshCheck`  |  Grants permission to refresh a Trusted Advisor check\.  | 
|  `SetAccountAccess`  |  Grants permission to enable or disable Trusted Advisor for the account\.  | 
|   `UpdateNotificationPreferences`   |  Grants permission to update notification preferences for Trusted Advisor\.  | 

### Trusted Advisor actions for organizational view<a name="trusted-advisor-organizational-view-actions"></a>

The following Trusted Advisor actions are for the organizational view feature\. For more information, see [Organizational view for AWS Trusted Advisor](organizational-view.md)\.


| Action | Description | 
| --- | --- | 
|  `DescribeOrganization`  |  Grants permission to view if the AWS account meets the requirements to enable the organizational view feature\.  | 
|  `DescribeOrganizationAccounts`  |  Grants permission to view the linked AWS accounts that are in the organization\.  | 
|  `DescribeReports`  |  Grants permission to view details for organizational view reports, such as the report name, runtime, date created, status, and format\.  | 
|  `DescribeServiceMetadata`  |  Grants permission to view information about organizational view reports, such as the AWS Regions, check categories, check names, and resource statuses\.  | 
|  `GenerateReport`  |  Grants permission to create a report for Trusted Advisor checks in your organization\.  | 
|  `ListAccountsForParent`  |  Grants permission to view, in the Trusted Advisor console, all of the accounts in an AWS organization that are contained by a root or organizational unit \(OU\)\.  | 
|  `ListOrganizationalUnitsForParent`  |  Grants permission to view, in the Trusted Advisor console, all of the organizational units \(OUs\) in a parent organizational unit or root\.  | 
|  `ListRoots`  |  Grants permission to view, in the Trusted Advisor console, all of the roots that are defined in an AWS organization\.  | 
|  `SetOrganizationAccess`  |  Grants permission to enable the organizational view feature for Trusted Advisor\.  | 

### AWS Trusted Advisor Priority actions<a name="trusted-advisor-priority-actions"></a>

You can perform the following Trusted Advisor actions in the console if you have AWS Trusted Advisor Priority enabled for your account, You can also add these Trusted Advisor actions in an IAM policy to allow or deny specific actions\. For more information, see [Example IAM policies for AWS Trusted Advisor Priority](#trusted-advisor-priority-policies)\.

**Note**  
The risks that appear in AWS Trusted Advisor Priority are recommendations that your technical account manager \(TAM\) has identified for your account\. Recommendations from a service, such as a Trusted Advisor check, are created for you automatically\. Recommendations from your TAM are created for you manually\. Next, your TAM sends these recommendations so that they appear in AWS Trusted Advisor Priority for your account\.

For more information, see [Get started with AWS Trusted Advisor Priority](trusted-advisor-priority.md)\.


| Action | Description | 
| --- | --- | 
|  `DescribeRisks`  |  Grants permission to view risks in AWS Trusted Advisor Priority\.  | 
|  `DescribeRisk`  |  Grants permission to view risk details in AWS Trusted Advisor Priority\.  | 
|  `DescribeRiskResources`  |  Grants permission to view affected resources for a risk in AWS Trusted Advisor Priority\.  | 
|  `UpdateRiskStatus`  |  Grants permission to update the risk status in AWS Trusted Advisor Priority\.  | 
|  `DownloadRisk`  |  Grants permission to download a file that contains details about the risk in AWS Trusted Advisor Priority\.  | 

## IAM policy examples<a name="iam-policy-examples-trusted-advisor"></a>

The following policies show you how to allow and deny access to Trusted Advisor\. You can use one of the following policies to create a *customer managed policy* in the IAM console\. For example, you can copy an example policy, and then paste it into the [JSON tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-json-editor) of the IAM console\. Then, you attach the policy to your IAM user, group, or role\.

For more information about how to create an IAM policy, see [Creating IAM policies \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) in the *IAM User Guide*\.

**Topics**
+ [Full access to Trusted Advisor](#full-access-trusted-advisor)
+ [Read\-only access to Trusted Advisor](#read-only-access-trusted-advisor)
+ [Deny access to Trusted Advisor](#no-access-trusted-advisor)
+ [Allow and deny specific actions](#allow-specific-actions-trusted-advisor)
+ [Control access to the AWS Support API operations for Trusted Advisor](#control-access-to-trusted-advisor-deny-support)
+ [Example IAM policies for AWS Trusted Advisor Priority](#trusted-advisor-priority-policies)
+ [Read\-only access to AWS Trusted Advisor Priority](#readonly-access-trusted-advisor-priority)
+ [Deny access to AWS Trusted Advisor Priority](#deny-access-trusted-advisor-priority)
+ [Allow and deny actions for AWS Trusted Advisor Priority](#allow-deny-access-trusted-advisor-priority)

### Full access to Trusted Advisor<a name="full-access-trusted-advisor"></a>

The following policy allows users to view and take all actions on all Trusted Advisor checks in the Trusted Advisor console\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:*",
            "Resource": "*"
        }
    ]
}
```

### Read\-only access to Trusted Advisor<a name="read-only-access-trusted-advisor"></a>

The following policy allows users read\-only access to the Trusted Advisor console\. Users can't make changes, such as refresh checks or change notification preferences\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:Describe*",
            "Resource": "*"
        }
    ]
}
```

### Deny access to Trusted Advisor<a name="no-access-trusted-advisor"></a>

The following policy doesn't allow users to view or take actions for Trusted Advisor checks in the Trusted Advisor console\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:*",
            "Resource": "*"
        }
    ]
}
```

### Allow and deny specific actions<a name="allow-specific-actions-trusted-advisor"></a>

The following policy allows users to view all Trusted Advisor checks in the Trusted Advisor console, but doesn't allow them to refresh any checks\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:RefreshCheck",
            "Resource": "*"
        }
    ]
}
```

### Control access to the AWS Support API operations for Trusted Advisor<a name="control-access-to-trusted-advisor-deny-support"></a>

In the AWS Management Console, a separate `trustedadvisor` IAM namespace controls access to Trusted Advisor\. You can't use the `trustedadvisor` namespace to allow or deny Trusted Advisor API operations in the AWS Support API\. Instead, you use the `support` IAM namespace\. You must have permissions to the AWS Support API to call Trusted Advisor programmatically\.

 For example, if you want to call the [RefreshTrustedAdvisorCheck](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html) operation, you must have permissions to this action in the policy\.

**Example : Allow Trusted Advisor API operations only**  
The following policy allows users access to the AWS Support API operations for Trusted Advisor, but not the rest of the AWS Support API operations\. For example, users can use the API to view and refresh checks\. They can't create, view, update, or resolve AWS Support cases\.   
You can use this policy to call the Trusted Advisor API operations programmatically, but you can't use this policy to view or refresh checks in the Trusted Advisor console\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "support:DescribeTrustedAdvisorCheckRefreshStatuses",
                "support:DescribeTrustedAdvisorCheckResult",
                "support:DescribeTrustedAdvisorChecks",
                "support:DescribeTrustedAdvisorCheckSummaries",
                "support:RefreshTrustedAdvisorCheck",
                "trustedadvisor:Describe*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": [
                "support:AddAttachmentsToSet",
                "support:AddCommunicationToCase",
                "support:CreateCase",
                "support:DescribeAttachment",
                "support:DescribeCases",
                "support:DescribeCommunications",
                "support:DescribeServices",
                "support:DescribeSeverityLevels",
                "support:ResolveCase"
            ],
            "Resource": "*"
        }
    ]
}
```

For more information about how IAM works with AWS Support and Trusted Advisor, see [Actions](security_iam_service-with-iam.md#security_iam_service-with-iam-id-based-policies-actions)\.

### Example IAM policies for AWS Trusted Advisor Priority<a name="trusted-advisor-priority-policies"></a>

You can use the following example policies to manage access to AWS Trusted Advisor Priority\. For more information, see [Get started with AWS Trusted Advisor Priority](trusted-advisor-priority.md)\.

#### Full access to AWS Trusted Advisor Priority<a name="full-access-trusted-advisor-priority"></a>

The following policy allows users full access to AWS Trusted Advisor Priority\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:DescribeRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:DownloadRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:UpdateRiskStatus",
            "Resource": "*"
        }
    ]
}
```

### Read\-only access to AWS Trusted Advisor Priority<a name="readonly-access-trusted-advisor-priority"></a>

The following policy allows read\-only access to AWS Trusted Advisor Priority\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:DescribeRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:DownloadRisk*",
            "Resource": "*"
        }
    ]
}
```

### Deny access to AWS Trusted Advisor Priority<a name="deny-access-trusted-advisor-priority"></a>

The following policy doesn't allow users access to AWS Trusted Advisor Priority\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:DescribeRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:DownloadRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:UpdateRiskStatus",
            "Resource": "*"
        }
    ]
}
```

### Allow and deny actions for AWS Trusted Advisor Priority<a name="allow-deny-access-trusted-advisor-priority"></a>

The following policy allows users to view a risk in AWS Trusted Advisor Priority but not download a file about the risk\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "trustedadvisor:DescribeRisk*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "trustedadvisor:DownloadRisk*",
            "Resource": "*"
        }
    ]
}
```

## See also<a name="see-also-security-trusted-advisor"></a>

For more information about Trusted Advisor permissions, see the following resources: 
+ [Actions defined by AWS Trusted Advisor](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awstrustedadvisor.html#awstrustedadvisor-actions-as-permissions) in the *IAM User Guide*\.
+ [Controlling Access to the Trusted Advisor Console](http://aws.amazon.com/premiumsupport/ta-iam/)