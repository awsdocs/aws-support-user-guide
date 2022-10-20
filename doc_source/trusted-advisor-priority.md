# Get started with AWS Trusted Advisor Priority<a name="trusted-advisor-priority"></a>

Trusted Advisor Priority helps you secure and optimize your AWS account to follow AWS best practices\. With Trusted Advisor Priority, your AWS account team can proactively monitor your account and create prioritized recommendations when they identify opportunities for you\. 

For example, your account team can identify if your root account lacks multi\-factor authentication \(MFA\)\. Your account team can create a recommendation so that you take immediate action on a check, such as `MFA on Root Account`\. The recommendation appears as an active *prioritized recommendation* on the Trusted Advisor Priority page of the Trusted Advisor console\. You then follow the recommendations to resolve the issue\.

Trusted Advisor Priority recommendations can come from either of two sources:
+ AWS services – Services such as Trusted Advisor, AWS Security Hub, and AWS Well\-Architected automatically create recommendations\. Your account team shares these recommendations with you so that they appear in Trusted Advisor Priority\.
+ Your account team – Your account team can create manual recommendations for risks that they identify in your account\.

Trusted Advisor Priority helps you focus on the most important recommendations\. You and your account team can keep track of the recommendation lifecycle, from the point when your account team shared the recommendation, up to the point when you accept, resolve, or reject it\. You can use Trusted Advisor Priority to find recommendations for all member accounts in your organization\.

**Topics**
+ [Prerequisites](#prerequisites-trusted-advisor-priority)
+ [Enable Trusted Advisor Priority](#enable-trusted-advisor-priority)
+ [View prioritized recommendations](#viewing-priority-recommendations)
+ [Accept a recommendation](#accepting-recommendations)
+ [Reject a recommendation](#rejecting-recommendation)
+ [Resolve a recommendation](#resolving-recommendations)
+ [Reopen a recommendation](#reopen-recommendations)
+ [Download recommendation details](#download-risk-details)
+ [Register delegated administrators](#register-delegated-administrators)
+ [Deregister delegated administrators](#deregister-delegated-administrators)
+ [Manage Trusted Advisor Priority notifications](#trusted-advisor-priority-notifications)
+ [Disable Trusted Advisor Priority](#disable-trusted-advisor-priority)

## Prerequisites<a name="prerequisites-trusted-advisor-priority"></a>

You must have the following requirements before you can use Trusted Advisor Priority: 
+ Your organization must have enabled all features for AWS Organizations\. This adds Trusted Advisor as a trusted service with Organizations\. You can enable trusted access from the **Your organization** page in the Trusted Advisor console or from Organizations\. For more information, see [Enabling all features in your organization ](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.
+ You must have an Enterprise Support plan and sign in to the organization's management account\.
+ You must have AWS Identity and Access Management \(IAM\) permissions to access Trusted Advisor Priority\. For information about how to control access to Trusted Advisor Priority, see [AWS managed policies for AWS Trusted Advisor](aws-managed-policies-for-trusted-advisor.md) and [Manage access for AWS Trusted Advisor](security-trusted-advisor.md)\.

## Enable Trusted Advisor Priority<a name="enable-trusted-advisor-priority"></a>

Contact your account team and ask that they enable this feature for you\. You must have an Enterprise Support plan and be the management account owner for your organization\.

## View prioritized recommendations<a name="viewing-priority-recommendations"></a>

After your account team enables Trusted Advisor Priority for your, you can view the latest recommendations for your organization\.

**To view your prioritized recommendations**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Priority** page, you can view the following:
   + **Actions needed** – The number of recommendations that are pending a response or in progress\.
   + **Overview** – The following information:
     + Rejected recommendations in the last 90 days
     + Resolved recommendations in the last 90 days
     + Recommendations without a status update in over 30 days
     + Average time to resolve recommendations

1. Under the **Active** tab, the **Active prioritized recommendations** show recommendations that your account team prioritized for you\.

   To filter your results, use the following options:
   + **Recommendation** – Enter keywords to search by name\. This can be a check name, or a custom name that your account team created\.
   + **Status** – Whether the recommendation is pending a response, in progress, rejected, or resolved\. 
   + **Source** – The origin of a prioritized recommendation\. The recommendation can come from AWS services, your AWS account team, or a planned service event\.
   + **Category** – The recommendation category, such as security or cost optimization\.
   + **Age** – When your account team shared the recommendation with you\.

1. Choose a recommendation to learn more about its risk details, affected resources and accounts that it impacts, and the recommended actions that you should take to resolve the issue\. You can then [accept](#accepting-recommendations) or [reject](#rejecting-recommendation) the recommendation\.

**Example : Trusted Advisor Priority recommendations**  
The following example shows recommendations available in Trusted Advisor Priority\.  

![\[Recommendation summary on the Trusted Advisor Priority console page.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-summary-2.png)

## Accept a recommendation<a name="accepting-recommendations"></a>

 Under the **Active** tab, you can learn more about the recommendation and then decide if you want to accept it\. When you accept a recommendation, you acknowledge the recommendation\.

**To accept a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Priority** page, under the **Active** tab, choose a recommendation name\.

1. On the recommendation detail page, review the information about the affected resources and accounts in your organization\.

1. Choose **Accept**\.

1. In the **Accept recommendation** dialog box, enter your name and title, and then choose **Accept**\.

   The recommendation status changes to **In progress**\. Recommendations in progress or pending a response appear in the **Active** tab on the Trusted Advisor Priority page\. 

1. Follow the steps in the recommendation details to address the issue\. You can then resolve the recommendation\. For more information, see [Resolve a recommendation](#resolving-recommendations)\.

**Example : Manual recommendation from Trusted Advisor Priority**  
The following image shows a recommendation that is pending a response\.  

![\[Accepted recommendation on the Trusted Advisor Priority console page.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-example-2.png)

## Reject a recommendation<a name="rejecting-recommendation"></a>

You can also reject a recommendation\. This means that you acknowledge the risk, but won't fix it now\. You can reject a recommendation if you don't think it's a risk, or if it's not relevant to your account\.

**To reject a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Priority** page, under the **Active** tab, choose a recommendation name\.

1. On the recommendation detail page, review the information and the affected resources and accounts in your organization\.

1. If this isn't a risk for your account, choose **Reject**\.

1. In the **Reject** dialog box, specify one of the following:
   + **Acknowledged – won't fix**
   + **Not a risk**

1. For **Reason for rejection**, enter a reason why you won't address the recommendation for now\.

1. Enter your name and title\.

1. Choose **Reject**\. The recommendation status changes to **Rejected** and appears in the **Closed** tab on the Trusted Advisor Priority page\.

    Trusted Advisor Priority also notifies your account team that you rejected the recommendation\.

**Example : Reject a recommendation from Trusted Advisor Priority**  
The following example shows a recommendation that isn't a risk to an account\.  

![\[Dialog box with dropdown lists to reject a recommendation in Trusted Advisor Priority.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-reject.png)

## Resolve a recommendation<a name="resolving-recommendations"></a>

After you accept and fix the risk, you can resolve the recommendation\.

**To resolve a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Priority** page, select the recommendation, and then choose **Resolve**\.

1. In the **Resolve recommendation** dialog box, enter your name and title\.

   Choose **Resolve**\. Resolved recommendations appear under the **Closed** tab on the Trusted Advisor Priority page\. Trusted Advisor Priority notifies your account team that you resolved the recommendation\.

**Example : Manual recommendation from Trusted Advisor Priority**  
The following example shows a manual recommendation from your account team\. The recommendation was then resolved\.  

![\[Recommendation description on Trusted Advisor Priority console page.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-example.png)

## Reopen a recommendation<a name="reopen-recommendations"></a>

After you resolve a recommendation, you or your account team can reopen the recommendation if there's another related risk to your account\.

**To reopen a recommendation**

1. On the **Trusted Advisor Priority** page, choose the **Closed** tab\.

1. Under **Closed recommendations**, select the recommendation, and then choose **Reopen**\.

1. In the **Reopen recommendation** dialog box, enter the following: 
   + Why you're reopening the recommendation
   + Your name
   + Your title

1. Choose **Reopen**\. The recommendation status changes to **In progress** and appears under the **Active** tab\.

1. Follow the steps in the recommendation details to address the issue\.

**Example : Reopen a recommendation from Trusted Advisor Priority**  
The following example shows a recommendation that you want to reopen\.  

![\[Dialog box to reopen a recommendation in Trusted Advisor Priority.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-reopen.png)

## Download recommendation details<a name="download-risk-details"></a>

You can also download the results of a prioritized recommendation from Trusted Advisor Priority\.

**Note**  
Currently, you can download only one recommendation at a time\.

**To download a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Priority** page, select the recommendation, and then choose **Download**\.

## Register delegated administrators<a name="register-delegated-administrators"></a>

You can add member accounts that are part of your organization as delegated administrators\. Delegated administrator accounts can review, accept, resolve, reject, and reopen recommendations in Trusted Advisor Priority\. 

After you register an account, you must grant the delegated administrator the required IAM permissions to access Trusted Advisor Priority\. For more information, see [Manage access for AWS Trusted Advisor](security-trusted-advisor.md) and [AWS managed policies for AWS Trusted Advisor](aws-managed-policies-for-trusted-advisor.md)\.

You can register up to five member accounts\. Only the management account can add delegated administrators for the organization\.

**To register a delegated administrator**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, under **Preferences**, choose **Your organization**\.

1. Under **Delegated administrator**, choose **Register new account**\.

1. In the dialog box, enter the member account ID, and then choose **Register**\. 

1. \(Optional\) To deregister an account, select an account and choose **Deregister**\. In the dialog box, choose **Deregister** again\. 

## Deregister delegated administrators<a name="deregister-delegated-administrators"></a>

When you deregister a member account, that account no longer has the same access to Trusted Advisor Priority as the management account\. Accounts that are no longer delegated administrators won't receive email notifications from Trusted Advisor Priority\.

**To deregister a delegated administrator**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, under **Preferences**, choose **Your organization**\.

1. Under **Delegated administrator**, select an account and choose **Deregister**\.

1. In the dialog box, choose **Deregister**\.

## Manage Trusted Advisor Priority notifications<a name="trusted-advisor-priority-notifications"></a>

Trusted Advisor Priority delivers notifications through email\. This email notification includes a summary of the recommendations that your account team prioritized for you\. You can specify the frequency that you receive updates from Trusted Advisor Priority\. 

If you registered member accounts as delegated administrators, they can also set up their accounts to receive Trusted Advisor Priority email notifications\.

Trusted Advisor Priority email notifications don't include check results for individual accounts and are separate from the Trusted Advisor dashboard weekly notification\. For more information, see [Set up notification preferences](get-started-with-aws-trusted-advisor.md#notification-preferences)\.

**To manage your Trusted Advisor Priority notifications**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, under **Preferences**, choose **Notifications**\.

1. Under **Trusted Advisor Priority**, you can select the following options\.

   1. **Daily** – Receive an email notification daily\.

   1. **Weekly** – Receive an email notification once a week\.

   1. Choose the notifications to receive:
      + Summary of prioritized recommendations
      + Resolution dates

1. For **Recipients**, select other contacts to receive the email notifications\. You can add and remove contacts from the [Account Settings](https://console.aws.amazon.com/billing/home#/account) page in the AWS Billing and Cost Management console\.

1. For **Language**, choose the language for the email notification\.

1. Choose **Save your preferences**\. 

**Note**  
Trusted Advisor Priority sends email notifications from the noreply@notifications\.trustedadvisor\.us\-west\-2\.amazonaws\.com address\. You might need to verify that your email client doesn't identify these emails as spam\.

## Disable Trusted Advisor Priority<a name="disable-trusted-advisor-priority"></a>

Contact your account team and ask that they disable this feature for you\. Prioritized recommendations no longer appear in your Trusted Advisor console\. 

If you disable Trusted Advisor Priority and then enable it again later, you can still view the recommendations that your account team sent before you disabled Trusted Advisor Priority\.