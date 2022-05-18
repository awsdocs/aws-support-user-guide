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

1. On the ** Dashboard** page, view the summary for each check category:
   + **Action recommended \(red\)** – Trusted Advisor recommends an action for the check\. For example, a check that detects a security issue for your IAM resources might recommend urgent steps\.
   + **Investigation recommended \(yellow\)** – Trusted Advisor detects a possible issue for the check\. For example, a check that reaches a quota for a resource might recommend ways to delete unused resources\.
   + **Excluded items \(gray\)** – The number of checks that have excluded items, such as resources that you want a check to ignore\. For example, this might be Amazon EC2 instances that you don't want the check to evaluate\.

1. You can do the following on the ** Dashboard** page:
   + To refresh all checks in your account, choose **Refresh all checks**\.
   + To create an \.xls file that includes all check results, choose **Download all checks**\.
   + Under **Checks summary**, choose a check category, such as **Security**, to view the results\.
   + Under **Potential monthly savings**, you can view how much you can save for your account and the cost optimization checks for recommendations\.
   + Under **Recent changes**, you can view changes to check statuses within the last 30 days\. Choose a check name to view the latest results for that check or choose the arrow icon to view the next page\.

**Example : Trusted Advisor Dashboard**  
The following example shows a summary of the check results\.  

![\[Screenshot of the dashboard page in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/trusted-advisor-dashboard-page.png)

## View check categories<a name="view-check-categories"></a>

You can view the check descriptions and results for the following check categories:
+ **Cost optimization** – Recommendations that can potentially save you money\. These checks highlight unused resources and opportunities to reduce your bill\.
+ **Performance** – Recommendations that can improve the speed and responsiveness of your applications\.
+ **Security** – Recommendations for security settings that can make your AWS solution more secure\.
+ **Fault tolerance** – Recommendations that help increase the resiliency of your AWS solution\. These checks highlight redundancy shortfalls, current service limits \(also known as quotas\), and overused resources\.
+ **Service limits** – Checks the usage for your account and whether your account approaches or exceeds the limit \(also known as quotas\) for AWS services and resources\. 

**To view check categories**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, choose the check category\.

1. On the category page, view the summary for each check category:
   + **Action recommended \(red\)** – Trusted Advisor recommends an action for the check\.
   + **Investigation recommended \(yellow\)** – Trusted Advisor detects a possible issue for the check\.
   + **No problems detected \(green\)** – Trusted Advisor doesn't detect an issue for the check\.
   + **Excluded items \(gray\)** – The number of checks that have excluded items, such as resources that you want a check to ignore\.

1. For each check, choose the refresh icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/refresh.png)\) to refresh this check\.

1. Choose the download icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/download.png)\) to create an \.xls file that includes the results for this check\.

**Example : Cost optimization category**  
The following example shows two \(yellow\) checks that need investigation and nine \(green\) checks that don't have any issues\.  

![\[Screenshot of the cost optimization category page in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/trusted-advisor-check-category-page.png)

## View specific checks<a name="view-specific-checks"></a>

Expand a check to view the full check description, your affected resources, any recommended steps, and links to more information\.

**To view a specific check**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane, choose a check category\.

1. Choose the check name to view the description and the following details:
   + **Alert Criteria** – Describes the threshold when a check will change status\.
   + **Recommended Action** – Describes the recommended actions for this check\.
   + **Additional Resources** – Lists related AWS documentation\.
   + A table that lists the affected items in your account\. You can include or exclude these items from check results\.

1. \(Optional\) To exclude items so that they don't appear in check results:

   1. Select an item and choose **Exclude & Refresh**\.

   1. To view all excluded items, choose **Excluded items**\.

1. \(Optional\) To include items so that the check evaluates them again:

   1. Choose **Excluded items**, select an item, and then choose **Include & Refresh**\.

   1. To view all included items, choose **Included items**\.

1. Choose the settings icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/settings.png)\) and in the **Preferences** dialog box, you can specify the number of items or the properties to display, and then choose **Confirm**\.

**Example : Cost optimization check**  
The following **Low Utilization Amazon EC2 Instances ** check lists the affected instances in the account\. This check identifies 41 Amazon EC2 instances that have low usage and recommends that you stop or terminate the resources\.  

![\[Screenshot of the Low Utilization Amazon EC2 Instances check in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/include-exclude-checks.png)

## Filter your checks<a name="filter-check-results"></a>

On the check category pages, you can specify which check results that you want to view\. For example, you might filter by checks that have detected errors in your account, so that you can investigate urgent issues first\.

If you have checks that evaluate items in your account, such as AWS resources, you can use tag filters to only show items that have the specified tag\.

**To filter your checks**

1. Sign in to the Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor/home](https://console.aws.amazon.com/trustedadvisor/home)\.

1. In the navigation pane or the **Dashboard** page, choose the check category\.

1. For **Search by keyword**, enter a keyword from the check name or description to filter your results\.

1. For the **View** list, specify which checks to view:
   + **All checks** – List all checks for this category
   + **Action recommended** – List checks that recommend that you take action\. These checks are highlighted in red\.
   + **Investigation recommended** – List checks that recommend that you take possible action\. These checks are highlighted in yellow\.
   + **No problems detected** – List checks that don't have any issues\. These checks are highlighted in green\.
   + **Checks with excluded items** – List checks that you specified to exclude items from the check results\.

1. If you added tags to your AWS resources, such as Amazon EC2 instances or AWS CloudTrail trails, you can filter your results so that the checks only show items that have the specified tag\.

   For **Filter by tag**, enter a tag key and value, and then choose **Apply filter**\.  
![\[Screenshot of the filter tags feature in the Trusted Advisor console.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/filter-by-tags.png)

1. In the table for the check, the check results only show items that have the specified key and value\.

1. To clear the filter by tags, choose **Reset**\.

### Related information<a name="related-information-for-tagging"></a>

For more information about tagging for Trusted Advisor, see the following topics:
+ [AWS Support enables tagging capabilities for Trusted Advisor](http://aws.amazon.com/about-aws/whats-new/2016/06/aws-support-enables-tagging-capabilities-for-trusted-advisor/)
+ [Tagging AWS resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the *AWS General Reference*

## Refresh check results<a name="refresh-check-results"></a>

You can refresh checks to get the latest results for your account\. If you have a Developer or Basic support plan, you can sign in to the Trusted Advisor console to refresh the checks\. If you have a Business, Enterprise On\-Ramp, or Enterprise Support plan, Trusted Advisor automatically refreshes the checks in your account on a weekly basis\.

**To refresh Trusted Advisor checks**

1. Navigate to the AWS Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor/)\.

1. On the ** Dashboard** or a check category page, choose **Refresh all checks**\.

You can also refresh specific checks in the following ways:
+ Choose the refresh icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/refresh.png)\) for an individual check\.
+ Use the [RefreshTrustedAdvisorCheck](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html) API operation\.

**Notes**  
Trusted Advisor automatically refreshes some checks several times a day, such as the **AWS Well\-Architected high risk issues for reliability** check\. It might take a few hours for changes to appear in your account\. For these automatically refreshed checks, you can't choose the refresh icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/refresh.png)\) to manually refresh your results\.
If you enabled AWS Security Hub for your account, you can't use the Trusted Advisor console to refresh Security Hub controls\. For more information, see [Refresh your Security Hub findings](security-hub-controls-with-trusted-advisor.md#refreshing-security-hub-findings)\.

## Download check results<a name="download-check-results"></a>

You can download check results to get an overview of Trusted Advisor in your account\. You can download results for all checks or a specific check\.

**To download Trusted Advisor checks results**

1. Navigate to the AWS Trusted Advisor console at [https://console\.aws\.amazon\.com/trustedadvisor](https://console.aws.amazon.com/trustedadvisor/)\.
   + To download all check results, in the ** Dashboard** or a check category page, choose **Download all checks**\.
   + To download a check result for a specific check, choose the check name, and then choose the download icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/download.png)\)

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

1. For **Weekly Email Notification**, select whom to notify for your check results\. You can add and remove contacts from the [Account Settings](https://console.aws.amazon.com/billing/home#/account) page in the AWS Billing and Cost Management console\.

1. For **Language**, choose the language for the email message\.

1. Choose **Save Email Preferences**\.

### Set up organizational view<a name="set-up-organizational-view"></a>

If you set up your account with AWS Organizations, you can create reports for all member accounts in your organization\. For more information, see [Organizational view for AWS Trusted Advisor](organizational-view.md)\.

### Disable Trusted Advisor<a name="disable-trusted-advisor"></a>

When you disable this service, Trusted Advisor won't perform any checks on your account\. Anyone who tries to access the Trusted Advisor console or use the API operations will receive an access denied error message\.

**To disable Trusted Advisor**

1. Under **Trusted Advisor**, choose **Disable Trusted Advisor**\. This action disables Trusted Advisor for all checks in your account\. 

1. You can then manually delete the [AWSServiceRoleForTrustedAdvisor](https://console.aws.amazon.com/iam/home?#/roles/AWSServiceRoleForTrustedAdvisor)  from your account\. For more information, see [Deleting a service\-linked role for Trusted Advisor](using-service-linked-roles-ta.md#delete-service-linked-role-ta)\.

### Related information<a name="related-information-getting-started"></a>

For more information about Trusted Advisor, see the following topics:
+ [How do I start using Trusted Advisor?](http://aws.amazon.com/premiumsupport/knowledge-center/trusted-advisor-intro/) 
+ [AWS Trusted Advisor check reference](trusted-advisor-check-reference.md)