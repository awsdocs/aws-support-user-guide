# Viewing AWS Security Hub controls in AWS Trusted Advisor<a name="security-hub-controls-with-trusted-advisor"></a>

After you enable AWS Security Hub for your AWS account, you can view your security controls and their findings in the Trusted Advisor console\. You can use Security Hub controls to identify security vulnerabilities in your account in the same way that you can use Trusted Advisor checks\. You can view the check's status, the list of affected resources, and then follow Security Hub recommendations to address your security issues\. You can use this feature to find security recommendations from Trusted Advisor and Security Hub in one convenient location\.

**Notes**  
From Trusted Advisor, you can view controls in the AWS Foundational Security Best Practices security standard *except* for controls that have the Category: Recover > Resilience\. For a list of supported controls, see [AWS Foundational Security Best Practices controls](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-fsbp-controls.html) in the *AWS Security Hub User Guide*\.  
For more information about the Security Hub categories, see [Control categories](https://docs.aws.amazon.com/securityhub/latest/userguide/control-categories.html)\.
Currently, when Security Hub adds new controls to the AWS Foundational Security Best Practices security standard, there can be a delay of two to four weeks before you can view them in Trusted Advisor\. This time frame is best effort and is not guaranteed\.

**Topics**
+ [Prerequisites](#prerequisites-security-hub)
+ [View your Security Hub findings](#security-controls-trusted-advisor-console)
+ [Refresh your Security Hub findings](#refreshing-security-hub-findings)
+ [Disable Security Hub from Trusted Advisor](#disable-security-hub)
+ [Troubleshooting](#troubleshooting-security-hub-integration)

## Prerequisites<a name="prerequisites-security-hub"></a>

You must meet the following requirements to enable the Security Hub integration with Trusted Advisor:
+ You must have a Business, Enterprise On\-Ramp, or Enterprise Support plan for this feature\. You can find your support plan from the [AWS Support Center](https://console.aws.amazon.com/support) or from the [Support plans](https://console.aws.amazon.com/support/plans) page\. For more information, see [Compare AWS Support plans](http://aws.amazon.com/premiumsupport/plans/)\.
+ You must enable resource recording in AWS Config for the AWS Regions that you want for your Security Hub controls\. For more information, see [Enabling and configuring AWS Config](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-prereq-config.html)\.
+ You must enable Security Hub and select the **AWS Foundational Security Best Practices v1\.0\.0** security standard\. If you haven't done so already, see [Setting up AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html) in the *AWS Security Hub User Guide*\.

**Note**  
If you already completed these prerequisites, you can skip to [View your Security Hub findings](#security-controls-trusted-advisor-console)\.

### About AWS Organizations accounts<a name="about-organizations-for-security-hub"></a>

If you already completed the prerequisites for a management account, this integration is enabled automatically for all member accounts in your organization\. Individual member accounts don't need to contact AWS Support to enable this feature\. However, member accounts in your organization must enable Security Hub if they want to see their findings in Trusted Advisor\. 

If you want to disable this integration for a specific member account, see [Disable this feature for AWS Organizations accounts](#disabling-security-hub-for-organizations)\.

## View your Security Hub findings<a name="security-controls-trusted-advisor-console"></a>

After you enable Security Hub for your account, it can take up to 24 hours for your Security Hub findings to appear in the **Security** page of the Trusted Advisor console\.

**To view your Security Hub findings in Trusted Advisor**

1. Navigate to the [Trusted Advisor console](https://console.aws.amazon.com/trustedadvisor), and then choose the **Security** category\.

1. In the **Search by keyword** field, enter the control name or description in the field\. 
**Tip**  
For **Source**, you can choose **AWS Security Hub** to filter for Security Hub controls\.

1. Choose the Security Hub control name to view the following information:
   + **Description** – Describes how this control checks your account for security vulnerabilities\.
   + **Source** – Whether the check comes from AWS Trusted Advisor or AWS Security Hub\. For Security Hub controls, you can find the control ID\.
   + **Alert Criteria** – The status of the control\. For example, if Security Hub detects an important issue, the status might be **Red: Critical or High**\.
   + **Recommended Action **– Use the Security Hub documentation link to find the recommended steps to fix the issue\.
   + **Security Hub resources** – You can find the resources in your account where Security Hub has detected an issue\.

**Notes**  
You must use Security Hub to exclude resources from your findings\. Currently, you can't use the Trusted Advisor console to exclude items from Security Hub controls\. For more information, see [Setting the workflow status for findings](https://docs.aws.amazon.com/securityhub/latest/userguide/finding-workflow-status.html)\.
The organizational view feature supports this integration with Security Hub\. You can view your findings for your Security Hub controls across your organization, and then create and download reports\. For more information, see [Organizational view for AWS Trusted Advisor](organizational-view.md)\.

**Example : Security Hub control for IAM user access key should not exist**  
The following is an example finding for a Security Hub control in the Trusted Advisor console\.  

![\[Screenshot a Security Hub control for an IAM root access issue.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/security-hub-control-example.png)

## Refresh your Security Hub findings<a name="refreshing-security-hub-findings"></a>

After you enable a security standard, it can take up to two hours for Security Hub to have findings for your resources\. It can then take up to 24 hours for that data to appear in the Trusted Advisor console\. If you recently enabled the **AWS Foundational Security Best Practices v1\.0\.0** security standard, check the Trusted Advisor console again later\.

**Note**  
The refresh schedule for each Security Hub control is *periodic* or *change triggered*\. Currently, you can't use the Trusted Advisor console or the AWS Support API to refresh your Security Hub controls\. For more information, see [Schedule for running security checks](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-schedule.html)\. 
You must use Security Hub if you want to exclude resources from your findings\. Currently, you can't use the Trusted Advisor console to exclude items from Security Hub controls\. For more information, see [Setting the workflow status for findings](https://docs.aws.amazon.com/securityhub/latest/userguide/finding-workflow-status.html)\.

## Disable Security Hub from Trusted Advisor<a name="disable-security-hub"></a>

Follow this procedure if you don't want your Security Hub information to appear in the Trusted Advisor console\. This procedure only disables the Security Hub integration with Trusted Advisor\. It won't affect your configurations with Security Hub\. You can continue to use the Security Hub console to view your security controls, resources, and recommendations\.

**To disable the Security Hub integration**

1. Contact [AWS Support](https://console.aws.amazon.com/support) and request to disable the Security Hub integration with Trusted Advisor\.

   After AWS Support disables this feature, Security Hub no longer sends data to Trusted Advisor\. Your Security Hub data will be removed from Trusted Advisor\. 

1. If you want to enable this integration again, contact [AWS Support](https://console.aws.amazon.com/support)\.

### Disable this feature for AWS Organizations accounts<a name="disabling-security-hub-for-organizations"></a>

If you already completed the previous procedure for a management account, Security Hub integration is automatically removed from all member accounts in your organization\. Individual member accounts in your organization don't need to contact AWS Support separately\.

If you're a member account in an organization, you can contact AWS Support to remove this feature from only your account\.

## Troubleshooting<a name="troubleshooting-security-hub-integration"></a>

If you're having issues with this integration, see the following troubleshooting information\.

**Contents**
+ [I don't see Security Hub findings in the Trusted Advisor console](#security-hub-findings-not-appearing)
+ [I configured Security Hub and AWS Config correctly, but my findings are still missing](#findings-still-not-appearing-after-enabling)
+ [I want to disable specific Security Hub controls](#missing-findings-for-some-checks)
+ [I want to find my excluded Security Hub resources](#finding-excluded-security-hub-findings)
+ [I want to enable or disable this feature for a member account that belongs to an AWS organization](#troubleshooting-organizations)
+ [I see multiple AWS Regions for the same affected resource for a Security Hub check](#multiple-regions-check-results)
+ [I turned off Security Hub or AWS Config in a Region](#disable-security-hub-regions)
+ [I still can't view my Security Hub findings](#security-hub-contact-support)

### I don't see Security Hub findings in the Trusted Advisor console<a name="security-hub-findings-not-appearing"></a>

Verify that you completed the following steps:
+ You have a Business, Enterprise On\-Ramp, or Enterprise Support plan\.
+ You enabled resource recording in AWS Config within the same Region as Security Hub\.
+ You enabled Security Hub and selected the **AWS Foundational Security Best Practices v1\.0\.0** security standard\.
+ New controls from Security Hub are added as checks in Trusted Advisor within two to four weeks\. See the [note](#best-effort-basis)\.

For more information, see the [Prerequisites](#prerequisites-security-hub)\.

### I configured Security Hub and AWS Config correctly, but my findings are still missing<a name="findings-still-not-appearing-after-enabling"></a>

It can take up to two hours for Security Hub to have findings for your resources\. It can then take up to 24 hours for that data to appear in the Trusted Advisor console\. Check the Trusted Advisor console again later\.

**Notes**  
Only your findings for controls in the AWS Foundational Security Best Practices security standard will appear in Trusted Advisor *except* for controls that have the **Category: Recover > Resilience**\.
If there's a service issue with Security Hub or Security Hub isn't available, it can take up to 24 hours for your findings to appear in Trusted Advisor\. Check the Trusted Advisor console again later\.

### I want to disable specific Security Hub controls<a name="missing-findings-for-some-checks"></a>

Security Hub sends your data to Trusted Advisor automatically\. If you disable a Security Hub control or no longer have resources for that control, your findings won't appear in Trusted Advisor\.

You can sign in to the [Security Hub console](https://console.aws.amazon.com/securityhub) and verify if your control is enabled or disabled\.

If you disable a Security Hub control or disable all controls for the AWS Foundational Security Best Practices security standard, your findings are archived within the next five days\. This five\-day period to archive is approximate and best effort only, and isn't guaranteed\. When your findings are archived, they are removed from Trusted Advisor\. 

For more information, see the following topics:
+ [Disabling and enabling individual controls](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-enable-disable-controls.html)
+ [Disabling or enabling a security standard](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-enable-disable.html)

### I want to find my excluded Security Hub resources<a name="finding-excluded-security-hub-findings"></a>

From the Trusted Advisor console, you can choose your Security Hub control name, and then choose the **Excluded items** option\. This option displays all resources that are suppressed in Security Hub\. 

If the workflow status for a resource is set to `SUPPRESSED`, then that resource is an excluded item in Trusted Advisor\. You can't suppress Security Hub resources from the Trusted Advisor console\. To do so, use the [Security Hub console](https://console.aws.amazon.com/securityhub)\. For more information, see [Setting the workflow status for findings](https://docs.aws.amazon.com/securityhub/latest/userguide/finding-workflow-status.html)\.

### I want to enable or disable this feature for a member account that belongs to an AWS organization<a name="troubleshooting-organizations"></a>

By default, member accounts inherit the feature from the management account for AWS Organizations\. If the management account has enabled the feature, then all accounts in the organization will also have the feature\. If you have a member account and want to make specific changes for your account, you must contact [AWS Support](https://console.aws.amazon.com/support)\.

### I see multiple AWS Regions for the same affected resource for a Security Hub check<a name="multiple-regions-check-results"></a>

Some AWS services are global and aren't specific to a Region, such as IAM and Amazon CloudFront\. By default, global resources such as Amazon S3 buckets appear in the US East \(N\. Virginia\) Region\.

For Security Hub checks that evaluate resources for global services, you might see more than one item for affected resources\. For example, if the `Hardware MFA should be enabled for the root user` check identifies that your account hasn't activated this feature, then you will see multiple Regions in the table for the same resource\. 

You can configure Security Hub and AWS Config so that multiple Regions won't appear for the same resource\. For more information, see [AWS Foundational Best Practices controls that you might want to disable](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-fsbp-to-disable.html)\.

### I turned off Security Hub or AWS Config in a Region<a name="disable-security-hub-regions"></a>

If you stop resource recording with AWS Config or disable Security Hub in an AWS Region, Trusted Advisor no longer receives data for any controls in that Region\. Your Security Hub data is removed from Trusted Advisor after 90 days\. This time frame is approximate and best effort only, and isn't guaranteed\. For more information, see [Disabling Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-disable.html)\.

To disable this feature for your account, see [Disable Security Hub from Trusted Advisor](#disable-security-hub)\.

### I still can't view my Security Hub findings<a name="security-hub-contact-support"></a>

If you still have issues with this feature, you can create a technical support case in the [AWS Support Center](https://console.aws.amazon.com/support/home)\.