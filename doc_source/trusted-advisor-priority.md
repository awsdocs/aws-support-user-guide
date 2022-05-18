# Get started with AWS Trusted Advisor Priority<a name="trusted-advisor-priority"></a>


****  

|  | 
| --- |
| AWS Trusted Advisor Priority is in preview release and is subject to change\. | 

AWS Trusted Advisor Priority helps you secure and optimize your account to better follow AWS best practices\. With AWS Trusted Advisor Priority, your technical account manager \(TAM\) can proactively monitor your AWS account and create prioritized recommendations when they identify risks\. For example, if your TAM identifies that you don't have multi\-factored authentication \(MFA\) activated for your root account, they can create a recommendation to take immediate action for the **MFA on Root Account** check\. You can find this risk as a *prioritized recommendation* on the AWS Trusted Advisor Priority page of the Trusted Advisor console\. 

AWS Trusted Advisor Priority recommendations can come from either of two sources:
+ AWS services – Services such as Trusted Advisor, AWS Security Hub, and AWS Well\-Architected automatically create recommendations\. Next, your TAM sends these recommendations so that they appear in your AWS Trusted Advisor Priority\.
+ Your TAM – Your TAM can create manual recommendations for risks that they identified in your account\.

AWS Trusted Advisor Priority helps you focus on the most important recommendations\. You and your TAM can keep track of the recommendation lifecycle, from the creation of a recommendation through when it is accepted, resolved, or rejected\. You can use AWS Trusted Advisor Priority to find recommendations for all member accounts in your AWS Organizations\.

**Notes**  
You must have an Enterprise Support plan and must sign in to the organization's management account to use AWS Trusted Advisor Priority\.
For information about controlling access to AWS Trusted Advisor Priority, see [Example IAM policies for AWS Trusted Advisor Priority](security-trusted-advisor.md#trusted-advisor-priority-policies)\.

**Topics**
+ [Enable AWS Trusted Advisor Priority](#enable-trusted-advisor-priority)
+ [View prioritized recommendations](#viewing-priority-recommendations)
+ [Accept a recommendation](#accepting-recommendations)
+ [Reject a recommendation](#rejecting-recommendation)
+ [Resolve a recommendation](#resolving-recommendations)
+ [Download recommendation details](#download-risk-details)
+ [Disable AWS Trusted Advisor Priority](#disable-trusted-advisor-priority)

## Enable AWS Trusted Advisor Priority<a name="enable-trusted-advisor-priority"></a>

Contact your TAM and ask that they enable this feature for you\. You must have an Enterprise Support plan and be the management account owner for your organization\.

## View prioritized recommendations<a name="viewing-priority-recommendations"></a>

Once your account has AWS Trusted Advisor Priority enabled, you can view the latest recommendations for your organization\.

**To view your prioritized recommendations**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **AWS Trusted Advisor Priority** page, you can view the following:
   + For **Actions needed**, you can see the number of recommendations that are waiting for your response or that are in progress\.
   + For **Overview**, you can see the number of recommendations for the following:
     + Rejected recommendations in the last 90 days
     + Resolved recommendations in the last 90 days
     + Recommendations without a status update in over 30 days
     + Average resolution time for recommendations

1. In the **Prioritized recommendations** section, you can view the recommendations that your TAM has prioritized for you\.

   You can filter the results by:
   + **Recommendation** – Enter keywords to search by recommendation name\. This can be a check name, or a custom name that your TAM created\.
   + **Status** – Whether the recommendation is pending a response, in progress, rejected, or resolved\. 
   + **Source** – The origin of a prioritized recommendation\. The recommendation can come from a service, manually added from your TAM, or a planned service event\.
   + **Category** – The recommendation category, such as security or cost optimization\.
   + **Age** – When your TAM shared the recommendation with you\.

1. Choose a recommendation name to learn more about its risk details, affected resources, and the recommended actions that you should take to resolve the recommendation\. You can then [accept](#accepting-recommendations) or [reject](#rejecting-recommendation) the recommendation\.

**Example : AWS Trusted Advisor Priority recommendations**  
The following image shows four manual recommendations that a TAM has sent to AWS Trusted Advisor Priority\.  

![\[Screenshot of recommendations on the AWS Trusted Advisor Priority page.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-summary-2.png)

## Accept a recommendation<a name="accepting-recommendations"></a>

Prioritized recommendations appear on the **AWS Trusted Advisor Priority** page\. From this page, you can accept a recommendation\. When you accept a recommendation, you acknowledge the risk and will address the issue\.

**To accept a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **AWS Trusted Advisor Priority** page, choose a recommendation name\.

1. On the recommendation details page, review information about this recommendation, as well as the affected resources within your organization\.

1. Choose **Accept**\.

1. In the **Accept recommendation** dialog box, enter your name and title, and then choose **Accept**\.

   The recommendation status changes to **In progress**\.

1. Follow the steps in the recommendation details to fix your issue\. You can then resolve the recommendation\. For more information, see [Resolve a recommendation](#resolving-recommendations)\.

**Example : Manual recommendation from AWS Trusted Advisor Priority**  
The following image shows a recommendation that has been accepted and is in progress\.  

![\[Screenshot of an accepted recommendation in AWS Trusted Advisor Priority.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-example-2.png)

## Reject a recommendation<a name="rejecting-recommendation"></a>

You can also reject a recommendation, which means that you acknowledge the risk, but choose not to fix the issue at this time\. You can reject a recommendation if you don't think it's a risk, or if the issue isn't relevant to your account\.

**To reject a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **AWS Trusted Advisor Priority** page, choose a recommendation name\.

1. On the recommendation details page, review information about this recommendation, as well as the affected resources within your organization\.

1. If this risk isn't an issue for your account, choose **Reject**\.

1. In the **Reject** dialog box, specify whether you acknowledge the issue and won't fix it, or if the issue isn't a risk to your account or organization\.

1. For **Reason for rejection**, enter a reason why you have chosen not to address this issue\.

1. Enter your name and title\.

1. Choose **Reject**\.

   The recommendation status changes to **Rejected**\. Your TAM will also be notified that you rejected their recommendation\.

## Resolve a recommendation<a name="resolving-recommendations"></a>

You can resolve a recommendation after you fix an issue\.

**Note**  
If you don't plan to fix an issue, you must accept the recommendation before you can resolve it\.

**To resolve a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **AWS Trusted Advisor Priority** page, select the recommendation, and then choose **Resolve**\.

1. In the **Resolve recommendation** dialog box, enter your name and title\.

   Choose **Resolve**\.

   The recommendation status changes to **Resolved**\. Your TAM will also be notified that you resolved their recommendation\.  
**Example : Manual recommendation from AWS Trusted Advisor Priority**  

   The following image shows a recommendation that your TAM has created and sent to your account, and that has been resolved\.  
![\[Screenshot of a specific recommendation in AWS Trusted Advisor Priority.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/ta-priority-recommendation-example.png)

## Download recommendation details<a name="download-risk-details"></a>

You can also download the results of a prioritized recommendation from AWS Trusted Advisor Priority\.

**Note**  
Currently, AWS Trusted Advisor Priority only supports downloading one recommendation at a time\.

**To download a recommendation**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **AWS Trusted Advisor Priority** page, select the recommendation, and then choose **Download**\.

## Disable AWS Trusted Advisor Priority<a name="disable-trusted-advisor-priority"></a>

Contact your TAM and ask that they disable this feature for you\. Once it's removed, the prioritized recommendations won't appear in your console\. 

If you disable AWS Trusted Advisor Priority and then enable it again later, you can still view the recommendations that your TAM sent prior to when you disabled AWS Trusted Advisor Priority\.