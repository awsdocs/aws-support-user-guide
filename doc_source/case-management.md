# Creating support cases and case management<a name="case-management"></a>

In the AWS Management Console, you can create three types of customer cases in AWS Support:
+ **Account and billing support** cases are available to all AWS customers\. You can get help with billing and account questions\.
+ **Service limit increase** requests are available to all AWS customers\. For more information about the default service quotas, formerly referred to as limits, see [AWS service quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *AWS General Reference*\.
+ **Technical support** cases connect you to technical support for help with service\-related technical issues and, in some cases, third\-party applications\. If you have a Developer Support plan, you can communicate by using email and the Support Center\. If you have a Business or Enterprise Support plan, you can also communicate by phone or live chat\.
**Note**  
If you have Basic Support, you can't create a technical support case\.
To change your support plan, see [Changing your AWS Support plan](changing-support-plans.md)\.
To close your account, see [Closing an Account](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/close-account.html) in the *AWS Billing and Cost Management User Guide*\.

## Creating a support case<a name="creating-a-support-case"></a>

You can create a support case in the Support Center of the AWS Management Console\.

**Notes**  
You can sign in to Support Center as the *root user* of your AWS account or as an AWS Identity and Access Management \(IAM\) user\. For more information, see [Access permissions for AWS Support](accessing-support.md)\.
If you can't sign in to Support Center and create a support case, you can use the [Contact Us](http://aws.amazon.com/contact-us/) page instead\. You can use this page to get help with billing and account issues\.

**To create a support case**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/)\.

2. In the top\-bar, choose **?** icon, and then choose **Support Center**\.

3. Choose **Create case**\.

4. Choose one of the following options:
   + **Account and billing support**
   + **Service limit increase**
   + **Technical support**

5. Follow the prompts to describe your case, such as the following:
   + Error messages that you received
   + Troubleshooting steps that you followed
   + How you're accessing the service:
     + AWS Management Console 
     + AWS Command Line Interface \(AWS CLI\)
     + API operations

6. Choose **Submit**\. Your case ID number and summary appear\.

## Example: Create a case for an Amazon EC2 instance<a name="case-example"></a>

As shown in the following screenshot, this example is a technical support case for an Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. 

![\[Screenshot of how to create a support case in the Support Center.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/support-create-case-console-1.png)

1. **Create case** – Choose the type of case to create from the three boxes at the top of the page\. In this example, the case type is **Technical support**\.
**Note**  
If you have the Basic Support plan, you can't create a technical support case\.

1. **Service** – If your question affects multiple services, choose the service that's most applicable\. In this example, the service is **Elastic Compute Cloud \(EC2 \- Linux\)**\.

1. **Category** – Choose the category that best fits your use case\. In this example, there's trouble connecting to an instance, so **Instance Issue** is chosen\. When you choose a category, links to information that might resolve your problem appear below the **Case classification** section\.

1. **Severity** – Customers with a paid support plan can choose the **General guidance** \(1\-day response time\) or **System impaired** \(12\-hour response time\) severity level\. Customers with a Business Support plan can also choose **Production system impaired** \(4\-hour response\) or **Production system down** \(1\-hour response\)\. Customers with Enterprise Support can choose **Business\-critical system down** \(15\-minute response\)\.

   Response times are for first response from AWS Support\. These response times don't apply to subsequent responses\. For third\-party issues, response times can be longer, depending on the availability of skilled personnel\. For more information, see [Choosing a severity](#choosing-severity)\.
**Note**  
Based on your category choice, you might be prompted for more information\. In this example, you're prompted to enter the **Instance ID**\. As a best practice, enter resource IDs, even when not prompted\.

After you specify the case type and classification, you can specify the description and how you want to be contacted\.

![\[Screenshot of how to create an Amazon EC2 support case in the Support Center.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/support-create-case-console-2.png)

1. **Subject** – Enter a title that briefly describes your issue\. In this example, the subject is **Failed status checks**\.

1. **Description** – This is the most important information that you provide to AWS Support\. For most service and category combinations, a prompt suggests information that's most helpful for the fastest resolution\. For more information, see [Describing your problem](#describing-your-problem)\.

1. **Attachments** – Screenshots and other attachments \(less than 5 MB each\) can be helpful\. In this example, the attached image is a failed status check\.

1. **Preferred contact language** – Currently, you can choose English or Japanese\.

1. **Contact methods** – Choose a contact method\. The options depend on the type of case and your support plan\. If you choose **Web**, you can read and respond to the case progress in Support Center\. If you have a Business or Enterprise Support plan, you can also choose **Chat** or **Phone**\. If you choose **Phone**, you're prompted for a callback number\.

1. **Additional contacts** – Enter the email addresses of people to be notified when the status of the case changes\. If you're signed in as an IAM user, include your email address\. If you're signed in with your email address and password, you don't need to include your email address\.
**Note**  
If you have the Basic Support plan, the **Additional contacts** box isn't available\. However, the **Operations** contact specified in the **Alternate Contacts** section of the [My Account](https://console.aws.amazon.com/billing/home?#/account) page receives copies of the case correspondence, but only for the specific case types of account and billing, and technical\.

1. Choose **Submit** when your information is complete and you're ready to create the case\.

## Describing your problem<a name="describing-your-problem"></a>

Make your description as detailed as possible\. Include relevant resource information, along with anything else that might help us understand your issue\. For example, to troubleshoot performance, include timestamps and logs\. For feature requests or general guidance questions, include a description of your environment and purpose\. In all cases, follow the **Description Guidance** that appears on your case submission form\.

When you provide as much detail as possible, you increase the chances that your case can be resolved quickly\.

## Choosing a severity<a name="choosing-severity"></a>

You might be inclined to always create a support case at the highest severity that your support plan allows\. However, we recommend that you choose the highest severities for cases that can't be worked around or that directly affect production applications\. For information about building your services so that losing single resources doesn't affect your applications, see the [Building Fault\-Tolerant Applications on AWS](http://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf) technical paper\.

The following table lists the severity levels, response times, and example problems\. 

**Note**  
You can't change the severity code for a support case after you create one\. If your situation changes, work with the AWS Support associate for your support case\. 


****  

| Severity | First\-response time | Description and support plan | 
| --- | --- | --- | 
|  **General guidance**  |  24 hours  |  You have a general development question, or you want to request a feature\. \(Developer\*, Business, and Enterprise Support plans\)  | 
|  **System impaired**  |  12 hours  |  Non\-critical functions of your application are behaving abnormally, or you have a time\-sensitive development question\. \(Developer\*, Business, and Enterprise Support plans\)  | 
|  **Production system impaired**  |  4 hours  |  Important functions of your application are impaired or degraded\. \(Business and Enterprise Support plans\)  | 
|  **Production system down**  |  1 hour  |  Your business is significantly impacted\. Important functions of your application aren't available\. \(Business and Enterprise Support plans\)  | 
| Business\-critical system down | 15 minutes |  Your business is at risk\. Critical functions of your application aren't available\. \(Enterprise Support plan\)  | 

\* For Developer Support, response targets are calculated in business hours\. Business hours are defined as 08:00 AM to 6:00 PM in the customer country, excluding holidays and weekends\. This information appears in the **Contact Information** section of the [My Account](https://console.aws.amazon.com/billing/home#/account) page in the AWS Management Console\. These times can vary in countries with multiple time zones\. Japanese support is available from 9:00 AM to 6:00 PM\.

**Note**  
We make every reasonable effort to respond to your initial request within the indicated timeframe\. For more information about the scope of support for each AWS Support plan, see [AWS Support features](https://aws.amazon.com/premiumsupport/features/)\.