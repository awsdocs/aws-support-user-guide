# Manage access for AWS Support Plans<a name="security-support-plans"></a>

**Topics**
+ [Permissions for the Support Plans console](#using-the-trusted-advisor-console)
+ [Support Plans actions](#support-plans-actions)
+ [Example IAM policies for Support Plans](#support-plans-policies)

## Permissions for the Support Plans console<a name="using-the-trusted-advisor-console"></a>

To access the Support Plans console, a user must have a minimum set of permissions\. These permissions must allow the user to list and view details about the Support Plans resources in your AWS account\.

You can create an AWS Identity and Access Management \(IAM\) policy with the `supportplans` namespace\. You can use this policy to specify permissions for actions and resources\.

When you create a policy, you can specify the namespace of the service to allow or deny an action\. The namespace for Support Plans is `supportplans`\.

You can use AWS managed policies and attach them to your IAM entities\. For more information, see [AWS managed policies for AWS Support Plans](managed-policies-aws-support-plans.md)\.

## Support Plans actions<a name="support-plans-actions"></a>

You can perform the following Support Plans actions in the console\. You can also specify these Support Plans actions in an IAM policy to allow or deny specific actions\. 


| Action | Description | 
| --- | --- | 
|  `GetSupportPlan`  |  Grants permission to view details about the current support plan for this AWS account\.  | 
|  `GetSupportPlanUpdateStatus`  |  Grants permission to view details about the status for a request to update a support plan\.  | 
|  `StartSupportPlanUpdate`  |  Grants permission to start the request to update the support plan for this AWS account\.  | 

## Example IAM policies for Support Plans<a name="support-plans-policies"></a>

You can use the following example policies to manage access to Support Plans\.

### Full access to Support Plans<a name="full-access-support-plans"></a>

The following policy allows users full access to Support Plans\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "supportplans:*",
            "Resource": "*"
        }
    ]
}
```

### Read\-only access to Support Plans<a name="readonly-access-support-plans"></a>

The following policy allows read\-only access to Support Plans\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "supportplans:Get*",
            "Resource": "*"
        }
    ]
}
```

### Deny access to Support Plans<a name="deny-access-support-plans"></a>

The following policy doesn't allow users access to Support Plans\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": "supportplans:*",
            "Resource": "*"
        }
    ]
}
```