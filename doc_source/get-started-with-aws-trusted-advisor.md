# Get started with AWS Trusted Advisor<a name="get-started-with-aws-trusted-advisor"></a>

You can access Trusted Advisor from the AWS Management Console\. Use the Trusted Advisor console to review check results for your AWS account and then follow the recommended steps to fix any issues\. For example, Trusted Advisor might recommend that you delete unused resources to reduce your monthly bill, such as an Amazon Elastic Compute Cloud \(Amazon EC2\) instance\.

You can also use the AWS Support API to perform operations on your Trusted Advisor checks\. For more information, see the [AWS Support API Reference](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html)\.

**Topics**
+ [Sign in to the Trusted Advisor console](#sign-in-the-trusted-advisor-console)
+ [View check categories](#view-check-categories)
+ [View specific checks](#view-specific-checks)
+ [Filter your checks](#filter-check-results)
+ [Refresh check results](#refresh-check-results)
+ [Download check results](#download-check-results)
+ [Organizational view](#set-up-organizational-view)
+ [Preferences](#preferences-trusted-advisor-console)

## Sign in to the Trusted Advisor console<a name="sign-in-the-trusted-advisor-console"></a>

You can view the checks and the status of each check in the Trusted Advisor console\.

**Note**  
You must have AWS Identity and Access Management \(IAM\) permissions to access the Trusted Advisor console\. For more information, see [Manage access for AWS Trusted Advisor](security-trusted-advisor.md)\.

**To sign in to the Trusted Advisor console**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. On the **Trusted Advisor Dashboard** page, view the summary for each check category\. Trusted Advisor uses the following color code for check results:
   + **Green** – Trusted Advisor doesn't detect an issue for the check\.
   + **Yellow** – Trusted Advisor detects a possible issue for the check\.
   + **Red** – Trusted Advisor recommends an action for the check\.

1. You can do the following on the **Trusted Advisor Dashboard** page:
   + To refresh all checks in your account, choose the refresh icon in the upper\-right corner\.
   + To create a \.xls file that includes all check results, choose the download icon in the upper\-right corner\.
   + To learn more about Trusted Advisor, choose the help pane icon in the upper\-right corner\.
   + Under **Recent Changes**, choose a check name to view the latest results for that check\.
   + Under **What's New**, choose a link for AWS blogs and resources to learn more about Trusted Advisor updates\.
   + Choose a check category to view the results, such as **Cost Performance**\.

**Example : Trusted Advisor Dashboard**  
The following example shows a summary of the check results\.  

![\[Screenshot of the dashboard page in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/trusted-advisor-dashboard-page.png)

## View check categories<a name="view-check-categories"></a>

You can view the check descriptions and results for the following check categories:
+ **Cost Optimization** – Recommendations that can potentially save you money\. These checks highlight unused resources and opportunities to reduce your bill\.
+ **Performance** – Recommendations that can improve the speed and responsiveness of your applications\.
+ **Security** – Recommendations for security settings that can make your AWS solution more secure\.
+ **Fault Tolerance** – Recommendations that help increase the resiliency of your AWS solution\. These checks highlight redundancy shortfalls, current service limits \(also known as quotas\), and overused resources\.
+ **Service Limits** – Checks the usage for your account and whether your account approaches or exceeds the limit \(also known as quotas\) for AWS services and resources\. 

**To view check categories**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane or the **Trusted Advisor Dashboard** page, choose the check category\.

1. For each check, such as **Low Utilization Amazon EC2 Instances**, choose the refresh icon to refresh this check\.

1. Choose the download icon to create a \.xls file that includes the results for this check\.

**Example : Cost Optimization category**  
The following example shows one \(yellow\) check that needs investigation and two \(green\) checks that don't\.  

![\[Screenshot of the Cost Optimization category page in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/trusted-advisor-check-category-page.png)

## View specific checks<a name="view-specific-checks"></a>

Expand a check to view the full check description, your affected resources, any recommended steps, and links for more resources\.

**To view a specific check**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane or the **Trusted Advisor Dashboard** page, choose the check category\.

1. Choose the check name to view the description and the following details:
   + **Alert Criteria** – Describes the threshold when a check will change status\.
   + **Recommended Action** – Describes the recommended actions for this check\.
   + **Additional Resources** – Lists related AWS documentation\.
   + A table that lists the affected resources in your account\. You can include or exclude these resources from check results\.

1. \(Optional\) To exclude resources so that they don't appear in check results:

   1. Select a resource and choose **Exclude & Refresh**\.

   1. To view all excluded resources, for **Item View**, choose **Excluded Items**\.

1. \(Optional\) To include resources so that the check evaluates them again:

   1. For **Item View**, choose **Excluded Items**, select a resource, and then choose **Include & Refresh**\.

   1. To view all included resources, for **Item View**, choose **Included Items**\.

1. Choose **Columns Display** and then select or clear the fields to appear for the resources\. 

**Example : Cost Optimization check**  
The following **Low Utilization Amazon EC2 Instances ** check lists the affected instances in the account\. This check identifies one Amazon EC2 instance that isn't used and recommends that you stop or terminate the resource\.  

![\[Screenshot of the Low Utilization Amazon EC2 Instances check in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/include-exclude-checks.png)

## Filter your checks<a name="filter-check-results"></a>

On the check category pages, you can specify which check results that you want to view\. For example, you might filter by checks that have detected errors in your account, so that you can investigate urgent issues first\.

If you have checks that evaluate items in your account, such as AWS resources, you can use tag filters to only show items that have the specified tag\.

**To filter your checks**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane or the **Trusted Advisor Dashboard** page, choose the check category\.

1. For the **View** list, specify which checks to view:
   + **All checks** – List all checks for this category
   + **No problems detected** – List checks that are green and don't have any issues
   + **Investigation recommended** – List checks that are yellow and recommend possible action
   + **Action recommended** – List checks that are red and recommend that you take action
   + **Checks with excluded items** – List checks that you specified to exclude items from the check results

1. If you added tags to your AWS resources, such as Amazon EC2 instances or AWS CloudTrail trails, you can filter your results so that the checks only show items that have the specified tag\.

   For **Filter by tag**, enter a tag key and value and then choose **Apply filter**\.

   For example, this filter uses the *trailtype* key and *allregions* value\.  
![\[Screenshot of the filter tags feature in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/filter-by-tags.png)

1. In the table for the check, the check results only show items that have the specified tag and value\.

   The following AWS CloudTrail Logging check shows three trails that have the specified *trailtype* key and the *allregions* value\.  
![\[Screenshot of tag results in the Trusted Advisor console for the AWS CloudTrail Logging check.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/filter-by-tags-cloudtrail-trails.png)

1. To clear the filter by tags, choose **Reset**\.

### Related information<a name="related-information-for-tagging"></a>

For more information about tagging for Trusted Advisor, see the following topics:
+ [AWS Support enables tagging capabilities for Trusted Advisor](http://aws.amazon.com/about-aws/whats-new/2016/06/aws-support-enables-tagging-capabilities-for-trusted-advisor/)
+ [Tagging AWS resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the *AWS General Reference*

## Refresh check results<a name="refresh-check-results"></a>

You can refresh checks to get the latest results for your account\. 

**To refresh Trusted Advisor checks**

1. Navigate to the AWS Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor/)\.

1. On the **Trusted Advisor Dashboard** or a check category page, choose the refresh icon in the upper\-right corner to refresh all checks\.

You can also refresh specific checks in the following ways:
+ Choose the refresh icon for an individual check\.
+ Use the [RefreshTrustedAdvisorCheck](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html) API operation\.

## Download check results<a name="download-check-results"></a>

You can download check results to get an overview of Trusted Advisor in your account\. You can download results for all checks or a specific check\.

**To download Trusted Advisor checks results**

1. Navigate to the AWS Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor/)\.
   + To download all check results, in the **Trusted Advisor Dashboard** or a check category page, choose the download icon in the upper\-right corner\.
   + To download a check result for a specific check, choose the check name, and then choose the download icon\.

1. Save or open the \.xls file\. The file contains the same summary information from the Trusted Advisor console, such as the check name, description, status, affected resources, and so on\.

## Organizational view<a name="set-up-organizational-view"></a>

You can set up the organizational view feature to create a report for all member accounts in your AWS organization\. For more information, see [Organizational view for AWS Trusted Advisor](organizational-view.md)\.

## Preferences<a name="preferences-trusted-advisor-console"></a>

On the **Preferences** page in the Trusted Advisor console, you can configure your weekly email messages for the check summary, enable the organizational view feature, or disable Trusted Advisor\.

### Set up notification preferences<a name="notification-preferences"></a>

Specify who can receive the weekly Trusted Advisor email messages for check results and the language\.

**To set up notification preferences**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, choose **Preferences**\.

1. For **Weekly Email Notification Preferences**, select whom to notify for your check results\. You can add and remove contacts from the [Account Settings](https://console.aws.amazon.com/billing/home#/account) page in the AWS Billing and Cost Management console\.

1. For **Notification Language**, choose the language for the email message\.

1. Choose **Save Email Preferences**\.

### Set up organizational view<a name="set-up-organizational-view"></a>

If you set up your account with AWS Organizations, you can create reports for all member accounts in your organization\. For more information, see [Organizational view for AWS Trusted Advisor](organizational-view.md)\.

### Disable Trusted Advisor<a name="disable-trusted-advisor"></a>

When you disable this service, Trusted Advisor won't perform any checks on your account\. Anyone who tries to access the Trusted Advisor console or use the API operations will receive an access denied error message\.

**To disable Trusted Advisor**

1. Under **TA Service Linked Role Permissions**, choose **Disable Trusted Advisor**\. This action disables Trusted Advisor for all checks in your account\. 

1. You can then manually delete the [AWSServiceRoleForTrustedAdvisor](https://console.aws.amazon.com/iam/home?#/roles/AWSServiceRoleForTrustedAdvisor) role from your account\. For more information, see [Deleting a service\-linked role for Trusted Advisor](using-service-linked-roles-ta.md#delete-service-linked-role-ta)\.

### Related information<a name="related-information-getting-started"></a>

For more information about Trusted Advisor, see the following topics:
+ [How do I start using Trusted Advisor?](http://aws.amazon.com/premiumsupport/knowledge-center/trusted-advisor-intro/) 
+ [AWS Trusted Advisor best practice checklist](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practice-checklist/)
