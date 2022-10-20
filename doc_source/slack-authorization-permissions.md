# Managing access to the AWS Support App widget<a name="slack-authorization-permissions"></a>

You can attach an AWS Identity and Access Management \(IAM\) policy to grant an IAM user permission to configure the AWS Support App widget in the AWS Support Center Console\.

For more information about how to add a policy to an IAM entity, see [Adding IAM identity permissions \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html#add-policies-console) in the IAM User Guide\.

**Note**  
You can also sign in as the root user in your AWS account, but we don't recommend that you do this\. For more information about root user access, see [Safeguard your root user credentials and don't use them for everyday tasks](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#lock-away-credentials) in the *IAM User Guide*\.

## Example IAM policy<a name="example-iam-policy-configure-support-center-console"></a>

You can attach the following policy to an entity, such as an IAM user or group\. This policy allows a user to authorize a Slack workspace and configure Slack channels in the Support Center Console\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "supportapp:GetSlackOauthParameters",
                "supportapp:RedeemSlackOauthCode",
                "supportapp:DescribeSlackChannels",
                "supportapp:ListSlackChannels",
                "supportapp:ListSlackWorkspaceConfigurations",
                "supportapp:ListSlackChannelConfigurations",
                "supportapp:ListSlackWorkspaces",
                "supportapp:CreateSlackChannelConfiguration",
                "supportapp:DeleteSlackChannelConfiguration",
                "supportapp:DeleteSlackWorkspaceConfiguration",
                "supportapp:GetAccountAlias",
                "supportapp:PutAccountAlias",
                "supportapp:DeleteAccountAlias",
                "supportapp:UpdateSlackChannelConfiguration",
                "iam:ListRoles"
            ],
            "Resource": "*"
        }
    ]
}
```