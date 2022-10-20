# Authorize a Slack workspace<a name="authorize-slack-workspace"></a>

After you authorize your workspace and give the AWS Support App permission to access it, you then need an AWS Identity and Access Management \(IAM\) role for your AWS account\. The AWS Support App uses this role to call API operations from [AWS Support](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html) and [Service Quotas](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/Welcome.html) for you\. For example, the AWS Support App uses the role to call the `CreateCase` operation to create a support case for you in Slack\.

**Notes**  
The Slack channel inherits permissions from the IAM role\. This means that any user in the Slack channel has the same permissions that are specified in the IAM policy that is attached to the role\.  
For example, if your IAM policy allows the role to have full read and write permissions to your support cases, anyone in your Slack channel can create, update, and resolve your support cases\. If your IAM policy allows the role read\-only permissions, then users in your Slack channel only have read permissions to your support cases\.
We recommend that you add the Slack workspaces and channels that you need to manage your support operations\. We recommend that you configure private channels and only invite required users\.

 You must authorize each Slack workspace that you want to use for your AWS account\. If you have multiple AWS accounts, you must sign in to each account and repeat the following procedure to authorize the workspace\. If your account belongs to an organization in AWS Organizations and you want to authorize multiple accounts, skip to [ Authorize multiple accounts](https://docs.aws.amazon.com/awssupport/latest/user/authorize-slack-workspace.html#authorize-multiple-accounts)\. 

**To authorize the Slack workspace for your AWS account**

1. Sign in to the [https://console.aws.amazon.com/support/app](https://console.aws.amazon.com/support/app) and choose **Slack configuration**\.

1. On the **Getting started** page, choose **Authorize workspace**\.

1. If you're not already signed in to Slack, on the **Sign in to your workspace** page, enter your workspace name, and then choose **Continue**\.

1. On the **AWS Support is requesting permission to access the your\-workspace\-name Slack** page, choose **Allow**\.
**Note**  
If you can't allow Slack to access your workspace, make sure that you have permissions from your Slack administrator to add the AWS Support App to the workspace\. See [Prerequisites](prerequisites-support-app-for-slack.md)\.

   On the **Slack configuration** page, your workspace name appears under **Workspaces**\.

1. \(Optional\) To add more workspaces, choose **Authorize workspace** and repeat steps 3\-4\. You can add up to five workspaces to your account\. 

1. \(Optional\) By default, your AWS account ID number appears as the account name in your Slack channel\. To change this value, under **Account name**, choose **Edit**, enter your account name, and then choose **Save**\. 
**Tip**  
Use a name that you and your team can easily recognize\. The AWS Support App uses this name to identify your account in the Slack channel\. You can update this name at any time\.  
![\[Screenshot of how to edit an account name so that it appears in the AWS Support App for Slack.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/edit-account-name.png)

   Your workspace and account name appear on the **Slack configuration** page\.  
![\[Slack workspace added to the AWS Support App configuration page.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/one-workplace-added-to-support-app.png)

## Authorize multiple accounts<a name="authorize-multiple-accounts"></a>

To authorize multiple AWS accounts to use Slack workspaces, contact AWS Support\. The member accounts must be part of the same organization in AWS Organizations\.

AWS Support adds the Slack workspaces for each account that you specify\. Each account can sign in to their [https://console.aws.amazon.com/support/app](https://console.aws.amazon.com/support/app) to find the workspace names under the **Workspaces** section\. These accounts don't need to authorize the workspaces that AWS Support already added\.

**Note**  
AWS Support doesn't create the IAM roles or configure the Slack channels for these accounts\. Instead, each account must complete the following tasks:  
Create an IAM role with the required permissions\. For more information, see [Managing access to the AWS Support App](support-app-permissions.md)\.
Configure a Slack channel to use the AWS Support App\. For more information, see [Configuring a Slack channel](add-your-slack-channel.md)\. To configure Slack channels programmatically, you can use the [AWS Support App in Slack API](https://docs.aws.amazon.com/supportapp/latest/APIReference/Welcome.html) or [AWS CloudFormation resources](creating-resources-with-cloudformation.md)\.

**To authorize multiple accounts**

1. Sign in to the [https://console.aws.amazon.com/support/app](https://console.aws.amazon.com/support/app) and choose **Slack configuration**\.

1. Choose **Add multiple accounts**\.

1. In the **Add multiple accounts** dialog box, choose [create a technical support case](https://support.console.aws.amazon.com/support/home#/case/create)\.

1. Choose the following options for your case:

   1. For related issue, choose **Technical**\.

   1.  For **Service**, choose **Support App in Slack** 

   1. For **Category**, choose **Other**\.

1. Choose **Next step: Additional information**\.

1. For **Additional information**, enter the following information:
   + The Slack workspace IDs that you want to add \(for example, `T012ABCDEFG`\)
   + The account IDs that you already added to the workspace
   + The account IDs that you want to add to the workspace

1. To create your case, follow the prompts\.

After AWS Support receives your request, AWS Support authorizes these accounts to use the Slack workspaces that you specified\.