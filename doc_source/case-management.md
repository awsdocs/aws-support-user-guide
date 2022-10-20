# Creating support cases and case management<a name="case-management"></a>

In the AWS Management Console, you can create three types of customer cases in AWS Support:
+ **Account and billing** support cases are available to all AWS customers\. You can get help with billing and account questions\.
+ **Service limit increase** requests are available to all AWS customers\. For more information about the default service quotas, formerly referred to as limits, see [AWS service quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *AWS General Reference*\.
+ **Technical** support cases connect you to technical support for help with service\-related technical issues and, in some cases, third\-party applications\. If you have Basic Support, you can't create a technical support case\.
**Notes**  
To change your support plan, see [Changing AWS Support Plans](changing-support-plans.md)\.
To close your account, see [Closing an Account](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/close-account.html) in the *AWS Billing User Guide*\.
If you're a customer of an AWS Partner that is part of the AWS Partner Network, and you use Resold Support, contact your AWS Partner directly for any billing related issues\. AWS Support can't assist with non\-technical issues for Resold Support, such as billing and account management\. For more information, see the following topics:   
[How AWS Partners can determine AWS Support plans in an organization](http://aws.amazon.com/blogs/mt/aws-partners-determine-aws-support-plans-in-organization/)
[AWS Partner\-Led Support](http://aws.amazon.com/premiumsupport/partner-led-support/)

## Creating a support case<a name="creating-a-support-case"></a>

You can create a support case in the Support Center of the AWS Management Console\.

**Notes**  
You can sign in to Support Center as the *root user* of your AWS account or as an AWS Identity and Access Management \(IAM\) user\. For more information, see [Manage access for AWS Support](accessing-support.md)\.
If you can't sign in to Support Center and create a support case, you can use the [Contact Us](http://aws.amazon.com/contact-us/) page instead\. You can use this page to get help with billing and account issues\.

**To create a support case**

1. Sign in to the [AWS Support Center Console](https://console.aws.amazon.com/support)\.
**Tip**  
In the AWS Management Console, you can also choose the question mark icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/questionmark.png)\) and then choose **Support Center**\.

1. Choose **Create case**\.

1. Choose one of the following options:
   + **Account and billing**
   + **Technical**
   + For service quota increases, choose **Looking for service limit increases?** and then follow the instructions for [Creating a service quota increase](create-service-quota-increase.md)\.

1. Choose the **Service**, **Category**, and **Severity**\.
**Tip**  
You can use the recommended solutions that appear for commonly asked questions\.

1. Choose **Next step: Additional information**

1. On the **Additional information** page, for **Subject**, enter a title about your issue\.

1. For **Description**, follow the prompts to describe your case, such as the following:
   + Error messages that you received
   + Troubleshooting steps that you followed
   + How you're accessing the service:
     + AWS Management Console 
     + AWS Command Line Interface \(AWS CLI\)
     + API operations

1. \(Optional\) Choose **Attach files** to add any relevant files to your case, such as error logs or screenshots\. You can attach up to three files\. Each file can be up to 5 MB\. 

1. Choose **Next step: Solve now or contact us**\.

1. On the **Contact us** page, choose your preferred language\. Currently, you can choose English or Japanese\. 

1. Choose your preferred contact method\. You can choose one of the following options:

   1. **Web** – Receive a reply in Support Center\.

   1. **Chat** – Start a live chat with a support agent\. If you can't connect to a chat, see [Troubleshooting](troubleshooting-support-cases.md)\.

   1. **Phone** – Receive a phone call from a support agent\. If you choose this option, enter the following information:
      + **Country or region**
      + **Phone number**
      + **\(Optional\) Extension**
**Notes**  
The contact options that appear depend on the type of case and your support plan\.
You can choose **Discard draft** to clear your support case draft\.

1. \(Optional\) If you have a Business, Enterprise On\-Ramp, or Enterprise Support plan, the **Additional contacts** option appears\. You can enter the email addresses of people to notify when the status of the case changes\. If you're signed in as an IAM user, include your email address\. If you're signed in with your root account email address and password, you don't need to include your email address
**Note**  
If you have the Basic Support plan, the **Additional contacts** option isn't available\. However, the **Operations** contact specified in the **Alternate Contacts** section of the [My Account](https://console.aws.amazon.com/billing/home?#/account) page receives copies of the case correspondence, but only for the specific case types of account and billing, and technical\.

1. Review your case details and then choose **Submit**\. Your case ID number and summary appear\.

## Describing your problem<a name="describing-your-problem"></a>

Make your description as detailed as possible\. Include relevant resource information, along with anything else that might help us understand your issue\. For example, to troubleshoot performance, include timestamps and logs\. For feature requests or general guidance questions, include a description of your environment and purpose\. In all cases, follow the **Description Guidance** that appears on your case submission form\.

When you provide as much detail as possible, you increase the chances that your case can be resolved quickly\.

## Choosing a severity<a name="choosing-severity"></a>

You might be inclined to always create a support case at the highest severity that your support plan allows\. However, we recommend that you choose the highest severities for cases that can't be worked around or that directly affect production applications\. For information about building your services so that losing single resources doesn't affect your applications, see the [Building Fault\-Tolerant Applications on AWS](http://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf) technical paper\.

The following table lists the severity levels, response times, and example problems\. 

**Notes**  
You can't change the severity code for a support case after you create one\. If your situation changes, work with the AWS Support for your support case\. 
For more information about the severity level, see the [AWS Support API Reference](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_SeverityLevel.html)\.


****  

| Severity | Severity level code | First\-response time | Description and support plan | 
| --- | --- | --- | --- | 
|  **General guidance**  | low |  24 hours  |  You have a general development question, or you want to request a feature\. \(Developer\*, Business, Enterprise On\-Ramp, or Enterprise Support plan\)  | 
|  **System impaired**  | normal |  12 hours  |  Non\-critical functions of your application are behaving abnormally, or you have a time\-sensitive development question\. \(Developer\*, Business, Enterprise On\-Ramp, or Enterprise Support plan\)  | 
|  **Production system impaired**  | high |  4 hours  |  Important functions of your application are impaired or degraded\. \(Business, Enterprise On\-Ramp, or Enterprise Support plan\)  | 
|  **Production system down**  | urgent |  1 hour  |  Your business is significantly impacted\. Important functions of your application aren't available\. \(Business, Enterprise On\-Ramp, or Enterprise Support plan\)  | 
| Business\-critical system down | critical | 15 minutes |  Your business is at risk\. Critical functions of your application aren't available \(Enterprise Support plan\)\. Note that this is 30 minutes for the Enterprise On\-Ramp Support plan\.  | 

\* For Developer Support, response targets are calculated in business hours\. Business hours are defined as 08:00 AM to 6:00 PM in the customer country, excluding holidays and weekends\. This information appears in the **Contact Information** section of the [My Account](https://console.aws.amazon.com/billing/home#/account) page in the AWS Management Console\. These times can vary in countries with multiple time zones\. Japanese support is available from 9:00 AM to 6:00 PM\.

**Note**  
We make every reasonable effort to respond to your initial request within the indicated timeframe\. For more information about the scope of support for each AWS Support plan, see [AWS Support features](https://aws.amazon.com/premiumsupport/features/)\.