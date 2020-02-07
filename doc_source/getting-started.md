# Getting Started with AWS Support<a name="getting-started"></a>

AWS Support offers a range of plans that provide access to tools and expertise that support the success and operational health of your AWS solutions\. All support plans provide 24x7 access to customer service, AWS documentation, whitepapers, and support forums\. For technical support and more resources to plan, deploy, and improve your AWS environment, you can select a support plan that best aligns with your AWS use case\.

## Features of AWS Support Plans<a name="features"></a>

AWS Support offers four support plans: Basic, Developer, Business, and Enterprise\. The Basic plan is free of charge and offers support for account and billing questions and service limit increases\. The other plans offer an unlimited number of technical support cases with pay\-by\-the\-month pricing and no long\-term contracts, providing the level of support that meets your needs\.

All AWS customers automatically have around\-the\-clock access to these features of the Basic support plan:
+ Customer Service: one\-on\-one responses to account and billing questions
+ Support forums
+ Service health checks
+ Documentation, whitepapers, and best\-practice guides

Customers with a Developer support plan have access to these additional features:
+ Best\-practice guidance
+ Building\-block architecture support: guidance on how to use AWS products, features, and services together
+ [AWS Identity and Access Management](#iam) \(IAM\) for controlling individuals' access to AWS Support

In addition, customers with a Business or Enterprise support plan have access to these features:
+ Use\-case guidance: what AWS products, features, and services to use to best support your specific needs\.
+ [AWS Trusted Advisor](#trusted-advisor), which inspects customer environments\. Then, Trusted Advisor identifies opportunities to save money, close security gaps, and improve system reliability and performance\.
+ An API for interacting with Support Center and Trusted Advisor\. This API allows for automated support case management and Trusted Advisor operations\.
+ Third\-party software support: help with Amazon Elastic Compute Cloud \(EC2\) instance operating systems and configuration\. Also, help with the performance of the most popular third\-party software components on AWS\.

In addition, customers with an Enterprise support plan have access to these features:
+ Application architecture guidance: consultative partnership supporting specific use cases and applications\.
+ Infrastructure event management: short\-term engagement with AWS Support to get a deep understanding of your use case—and after analysis, provide architectural and scaling guidance for an event\.
+ Technical account manager
+ White\-glove case routing
+ Management business reviews

For more detailed information about features and pricing for each support plan, see [AWS Support](https://aws.amazon.com/premiumsupport/) and [AWS Support Features](https://aws.amazon.com/premiumsupport/features/)\. Some features, such as around\-the\-clock phone and chat support, aren't available in all languages\.

## Case Management<a name="case-management"></a>

You can sign in to the Support Center at [https://console\.aws\.amazon\.com/support/home\#/](https://console.aws.amazon.com/support/home#/) by using the email address and password linked to your AWS account\. To log in with other credentials, see [Accessing AWS Support](#accessing-support)\.

There are three types of cases you can open:
+ **Account and Billing Support** cases are available to all AWS customers\. This case type connects you to customer service for help with billing and account\-related questions\.
+ **Service Limit Increase** requests are also available to all AWS customers\. For information on the default service limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\.
+ **Technical Support** cases connect you to technical support for help with service\-related technical issues and, in some cases, third\-party applications\. If you have a Developer support plan, you can communicate using the web\. If you have a Business or Enterprise support plan, you can also communicate by phone or live chat\.

To open a Support case:
+ In [Support Center](https://console.aws.amazon.com/support/home#/), choose the **Create case** button\.

### Example: Creating a Case<a name="case-example"></a>

Here is an example of a Technical Support case \(shown in two parts for readability\)\. The lists that follow the form example explain some of your options and best practices\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/support-create-case-console-1.png)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/)
+ **Service**\. If your question affects multiple services, choose the service that's most applicable\. In this case, select **Elastic Compute Cloud \(EC2 \- Linux\)**\.
+ **Category**\. Choose the category that best fits your use case\. In this case, there's trouble connecting to an instance, so choose **Instance Issue**\. When you select a category, links to information that might help to resolve your problem appear below the **Category** selection\.
+ **Severity**\. Customers with a paid support plan can choose the **General guidance** \(1\-day response time\) or **System impaired** \(12\-hour response time\) severity level\. Customers with a Business support plan can also choose **Production system impaired** \(4\-hour response\) or **Production system down** \(1\-hour response\)\. And customers with an Enterprise plan can choose **Business\-critical system down** \(15\-minute response\)\.

  Response times are for first response from AWS Support\. These response times don't apply to subsequent responses\. For third\-party issues, response times can be longer, depending on the availability of skilled personnel\. For details, see [Choosing a Severity](#choosing-severity)\.
**Note**  
Based on your category choice, you might be prompted for additional information\. In this case, you're prompted to provide the **Instance IDs**\. In general, it's a good idea to provide resource IDs, even when not prompted\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/images/support-create-case-console-2.png)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/awssupport/latest/user/)
+ **Subject**\. Treat this like the subject of an email message—briefly describe your issue\. In this case, use the subject `Failed status checks`\.
+ **Description**\. This is the most important information that you provide to AWS Support\. For most service and category combinations, a prompt suggests information that's most helpful for the fastest resolution\. For more guidance, see [Describing Your Problem](#describing-your-problem)\.
+ **Attachments**\. Screen shots and other attachments \(less than 5 MB each\) can be helpful\. In this case, an image is added that shows the failed status check\.
+ **Contact methods**\. Select a contact method\. The options vary depending on the type of case and your support plan\. If you choose **Web**, you can read and respond to the case progress in Support Center\. If you have a Business or Enterprise support plan, you can also select **Chat** or **Phone**\. If you select **Phone**, you're prompted for a callback number\.
+ **Additional contacts**\. Provide the email addresses of people to be notified when the status of the case changes\. If you're signed in as an IAM user, include your own email address\. If you're signed in with your email address and password, you don't need to include your email address in this box\.
**Note**  
If you have the Basic support plan, the **Additional contacts** box isn't available\. However, the **Operational** contact specified in the **Alternate Contacts** section of the [My Account](https://console.aws.amazon.com/billing/home?#/account) page receives copies of the case correspondence, but only for the specific case types of Account, Billing, and Technical\.
+ **Case Type**\. Select the type of case you want to create from the three boxes at the top of the page\. In this example, select **Technical Support**\.
**Note**  
If you have the Basic support plan, you can't create a technical support case\.
+ **Submit**\. Choose **Submit** when your information is complete\. Choosing **Submit** creates the case\.

#### Choosing a Severity<a name="choosing-severity"></a>

You might want to always open cases at the highest severity allowed by your support plan\. However, we strongly encourage that you limit the use of the highest severities to cases that can't be worked around or that directly affect production applications\. Plan ahead to avoid high\-severity cases for general guidance questions\. For information about building your services so that losing single resources doesn't affect your application, see [Building Fault\-Tolerant Applications on AWS](http://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf)\.

Here is a summary of severity levels, response times, and example problems\. For more information about the scope of support for each AWS Support plan, see [AWS Support Features](https://aws.amazon.com/premiumsupport/features/)\. **Note**: We make every reasonable effort to respond to your initial request within the indicated timeframe\.


****  

| Severity | First\-Response Time | Description / Support Plan | 
| --- | --- | --- | 
| General guidance | 24 hours | You have a general development question, or you want to request a feature\. \(Developer\*, Business, and Enterprise support plans\) | 
| System impaired | 12 hours | Non\-critical functions of your application are behaving abnormally, or you have a time\-sensitive development question\. \(Developer\*, Business, and Enterprise support plans\) | 
| Production system impaired | 4 hours | Important functions of your application are impaired or degraded\. \(Business and Enterprise support plans\) | 
| Production system down | 1 hour | Your business is significantly impacted\. Important functions of your application aren't available\. \(Business and Enterprise support plans\) | 
| Business\-critical system down | 15 minutes | Your business is at risk\. Critical functions of your application aren't available\. \(Enterprise support plan\) | 

\* For the Developer plan, response targets are calculated in business hours\. Business hours are defined as 8:00 AM to 6:00 PM in the customer country, as set in the contact information of [My Account](https://console.aws.amazon.com/billing/home#/account), excluding holidays and weekends\. These times can vary in countries with multiple time zones\. Note that Japanese support is available from 9:00 AM to 6:00 PM\.

#### Describing Your Problem<a name="describing-your-problem"></a>

Make your description as detailed as possible\. Include relevant resource information, along with anything else that might help us understand your issue\. For example, to troubleshoot performance, include time stamps and logs\. For feature requests or general guidance questions, include a description of your environment and purpose\. In all cases, follow the **Description Guidance** that appears on your case submission form\.

When you provide as much detail as possible, you increase the chances that your case can be resolved quickly\.

### Monitoring and Maintaining Your Case<a name="monitoring-your-case"></a>

You can monitor the status of your case in Support Center\. A new case begins in the `Unassigned` state\. When an engineer begins work on a case, the status changes to `Work in Progress.` The engineer responds to your case, either to ask for more information \(`Pending Customer Action`\) or to let you know that the case is being investigated \(`Pending Amazon Action`\)\.

When your case is updated, you receive email with the correspondence and a link to the case in Support Center—you can't respond to case correspondence by email\. When you're satisfied with the response or your problem is solved, you can select **Close Case** in Support Center\. If you don't respond within ten days, the case is closed automatically\. You can always reopen a resolved or closed case\.

Be sure to create a new case for a new issue or question\. If case correspondence strays from the original question or issue, a support engineer might ask you to open a new case\. If you open a case related to old inquiries, include \(where possible\) the related case number so that we can refer to previous correspondence\.

### Case History<a name="case-history"></a>

Case history information is available for 12 months after creation\.

## Accessing AWS Support<a name="accessing-support"></a>

There are two ways to access Support Center:
+ Use the email address and password associated with your AWS account
+ Use AWS Identity and Access Management \(Preferred\)

Customers with a Business or Enterprise support plan can also access AWS Support and Trusted Advisor operations programmatically by using the [AWS Support API](Welcome.md)\.

### AWS Account<a name="root-account"></a>

You can use your AWS account information to access Support Center\. Sign in at [https://console\.aws\.amazon\.com/support/home\#/](https://console.aws.amazon.com/support/home#/), and then enter your email address and password\. However, avoid using this method as much as possible\. Instead, use IAM\. For more information, see [Lock away your AWS account access keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html#lock-away-credentials)\.

### IAM<a name="iam"></a>

You can use IAM to create individual users or groups, and then give them permission to perform actions and access resources in Support Center\.

**Note**  
IAM users who are granted Support access can see all the cases that are created for the account\.

By default, IAM users can't access the Support Center\. You can give users access to your account’s Support resources \(Support Center cases and the AWS Support API\) by attaching IAM policies to users, groups, or roles\. For more information, see [IAM Users and Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/Using_WorkingWithGroupsAndUsers.html) and [Overview of AWS IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/PoliciesOverview.html)\.

After you create IAM users, you can give those users individual passwords\. They can then sign in to your account and work in Support Center by using an account\-specific sign\-in page\. For more information, see [How IAM Users Sign In to Your AWS Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/WhatUsersNeedToKnow.html)\.

The easiest way to grant permission is to attach the AWS managed policy `AWSSupportAccess` to the user, group, or role\. Support allows action\-level permissions to control access to specific Support operations\. However, Support does not provide resource\-level access, so the `Resource` element is always set to `*`\. An IAM user with Support permissions has access to all Support operations and resources\.

For example, this policy statement grants an IAM user access to Support:

```
{
  "Version": "2012-10-17",
  "Statement": [
  {
    "Effect": "Allow",
    "Action": "support:*",
    "Resource": "*"
  }]
}
```

This policy statement allows an IAM user to do everything except resolve a case:

```
{
   "Version": "2012-10-17",
   "Statement": [
   {
      "Effect": "Allow",
      "Action": "support:",
      "Resource": "*"
   },
   {
       "Effect": "Deny",
       "Action": "support:ResolveCase",
       "Resource": "*"
    }]
}
```

If the user or group already has a policy, you can add the Support\-specific policy statement illustrated here to that policy\.

**Note**  
Access to Trusted Advisor in the AWS Management Console is controlled by a separate `trustedadvisor` IAM namespace\. Access to Trusted Advisor with the AWS Support API is controlled by the `support` IAM namespace\. For more information, see [Controlling Access to the Trusted Advisor Console](https://aws.amazon.com/premiumsupport/trustedadvisor/ta-iam/)\.

## AWS Trusted Advisor<a name="trusted-advisor"></a>

[AWS Trusted Advisor](https://console.aws.amazon.com/trustedadvisor/) draws upon best practices learned from serving hundreds of thousands of AWS customers\. Trusted Advisor inspects your AWS environment, and then makes recommendations when opportunities exist to save money, improve system availability and performance, or help close security gaps\. All AWS customers have access to five Trusted Advisor checks\. Customers with a Business or Enterprise support plan can view all Trusted Advisor checks\. For more information, see [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/trustedadvisor/)\.

For information about using Amazon CloudWatch Events to monitor the status of Trusted Advisor checks, see [Monitoring Trusted Advisor Check Results with Amazon CloudWatch Events](cloudwatch-events-ta.md)\. 

Customers can access Trusted Advisor in the AWS Management Console\. Programmatic access to Trusted Advisor is available with the [AWS Support API](Welcome.md)\.

## Troubleshooting<a name="troubleshooting"></a>

For answers to common troubleshooting questions, see the [AWS Support Knowledge Center](https://aws.amazon.com/premiumsupport/knowledge-center)\.

For Windows, Amazon EC2 offers EC2Rescue, which allows customers to examine their Windows instances to help identify common problems, collect log files, and help AWS Support to troubleshoot your issues\. You can also use EC2Rescue to analyze boot volumes from non\-functional instances\. For more information, see [How can I use EC2Rescue to troubleshoot and fix common issues on my EC2 Windows instance?](https://aws.amazon.com/premiumsupport/knowledge-center/ec2rescue-windows-troubleshoot/)

### Service\-specific Troubleshooting<a name="service-troubleshooting"></a>

Most AWS service documentation contains troubleshooting topics that can get you started before contacting Support\. The following table provides links to troubleshooting topics, arranged by service\.


****  

| Service | Link | 
| --- | --- | 
| Amazon Web Services | [Troubleshooting AWS Signature Version 4 Errors](https://docs.aws.amazon.com/general/latest/gr/signature-v4-troubleshooting.html) | 
| Amazon AppStream | [Troubleshoot Amazon AppStream](https://docs.aws.amazon.com/appstream2/latest/developerguide/troubleshooting.html) | 
| Amazon EC2 Auto Scaling | [Troubleshooting Auto Scaling](https://docs.aws.amazon.com/autoscaling/latest/userguide/CHAP_Troubleshooting.html) | 
| AWS Certificate Manager \(ACM\) | [Troubleshooting](https://docs.aws.amazon.com/acm/latest/userguide/troubleshooting.html) | 
| AWS CloudFormation | [Troubleshooting AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html) | 
| Amazon CloudFront | [Troubleshooting](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Troubleshooting.html) \| [Troubleshooting RTMP Distributions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Streaming_Troubleshooting.html)  | 
| AWS CloudHSM | [Troubleshooting](https://docs.aws.amazon.com/cloudhsm/latest/userguide/cloud-hsm-troubleshooting.html) | 
| Amazon CloudSearch | [Troubleshooting Amazon CloudSearch](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/troubleshooting.html) | 
| AWS CodeDeploy | [Troubleshooting AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/troubleshooting.html) | 
| AWS Data Pipeline | [Troubleshooting](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-troubleshooting.html) | 
| AWS Direct Connect | [Troubleshooting AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Troubleshooting.html) | 
| AWS Directory Service | [Troubleshooting AWS Directory Service Administration Issues](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/admin_troubleshooting.html) | 
| Amazon DynamoDB | [Troubleshooting](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBPipeline.html#DataPipelineExportImport.Troubleshooting) | 
| AWS Elastic Beanstalk | [Troubleshooting](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/troubleshooting.html) | 
| Amazon Elastic Compute Cloud \(Amazon EC2\) | [Troubleshooting Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-troubleshoot.html) \| [Troubleshooting Windows Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/troubleshooting-windows-instances.html) \| [Troubleshooting VM Import/Export](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/VMImportTroubleshooting.html) \| [Troubleshooting API Request Errors](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/query-api-troubleshooting.html) \| [Troubleshooting the AWS Management Pack](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/TroubleshootingAWSmp.html) \| [Troubleshooting AWS Systems Manager for Microsoft SCVMM](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/scvmm-troubleshoot.html) \| [AWS Diagnostics for Microsoft Windows Server](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/Windows-Server-Diagnostics.html)  | 
| Amazon Elastic Container Service \(Amazon ECS\) | [Amazon ECS Troubleshooting](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/troubleshooting.html) | 
| Elastic Load Balancing | [Troubleshoot Your Application Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-troubleshooting.html) \| [Troubleshoot Your Classic Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-troubleshooting.html) | 
| Amazon EMR \(Amazon EMR\) | [Troubleshoot a Cluster](https://docs.aws.amazon.com/emr/latest/DeveloperGuide/emr-troubleshoot.html) | 
| Amazon ElastiCache for Memcached | [Troubleshooting Applications](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/Troubleshooting.html) | 
| Amazon ElastiCache for Redis | [Troubleshooting Applications](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Troubleshooting.html) | 
| AWS Flow Framework | [Troubleshooting and Debugging Tips](https://docs.aws.amazon.com/amazonswf/latest/awsflowguide/troubleshooting.html) | 
| AWS GovCloud \(US\) | [Troubleshooting](https://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-troubleshooting.html) | 
| AWS Identity and Access Management \(IAM\) | [Troubleshooting IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/iam-troubleshooting.html) | 
| Kinesis | [Troubleshooting Amazon Kinesis Streams Producers](https://docs.aws.amazon.com/kinesis/latest/dev/troubleshooting-producers.html) \| [Troubleshooting Amazon Kinesis Streams Consumers](https://docs.aws.amazon.com/kinesis/latest/dev/troubleshooting-consumers.html) | 
| AWS Lambda | [Troubleshooting and Monitoring AWS Lambda Functions with CloudWatch](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-functions.html) | 
| AWS OpsWorks | [Debugging and Troubleshooting Guide](https://docs.aws.amazon.com/opsworks/latest/userguide/troubleshoot.html) | 
| Amazon Redshift | [Troubleshooting Queries](https://docs.aws.amazon.com/redshift/latest/dg/queries-troubleshooting.html) \| [Troubleshooting Data Loads](https://docs.aws.amazon.com/redshift/latest/dg/t_Troubleshooting_load_errors.html) \| [Troubleshooting Connection Issues in Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/mgmt/troubleshooting-connections.html) \| [Troubleshooting Amazon Redshift Audit Logging](https://docs.aws.amazon.com/redshift/latest/mgmt/db-auditing.html#db-auditing-failures) | 
| Amazon Relational Database Service \(Amazon RDS\) | [Troubleshooting](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Troubleshooting.html) \| [Troubleshooting Applications](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/APITroubleshooting.html) | 
| Amazon Route 53 | [Troubleshooting Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/troubleshooting-route-53.html) | 
| Amazon Silk | [Troubleshooting](https://docs.aws.amazon.com/silk/latest/developerguide/troubleshooting.html) | 
| Amazon Simple Email Service \(Amazon SES\) | [Troubleshooting Amazon SES](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/troubleshooting.html) | 
| Amazon Simple Storage Service \(Amazon S3\) | [Troubleshooting CORS Issues](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors-troubleshooting.html) \| [Handling REST and SOAP Errors](https://docs.aws.amazon.com/AmazonS3/latest/dev/HandlingErrors.html) | 
| Amazon Simple Workflow Service \(Amazon SWF\) | [AWS Flow Framework for Java: Troubleshooting and Debugging Tips](https://docs.aws.amazon.com/amazonswf/latest/awsflowguide/troubleshooting.html) \| [AWS Flow Framework for Ruby: Troubleshooting and Debugging Workflows](https://docs.aws.amazon.com/amazonswf/latest/awsrbflowguide/programming-troubleshooting.html) | 
| AWS Storage Gateway | [Troubleshooting Your Gateway](https://docs.aws.amazon.com/storagegateway/latest/userguide/Troubleshooting-common.html) | 
| Amazon Virtual Private Cloud \(Amazon VPC\) | [Troubleshooting](https://docs.aws.amazon.com/vpc/latest/adminguide/Troubleshooting.html) | 
| Amazon WorkMail | [Troubleshooting the Amazon WorkMail Web Application](https://docs.aws.amazon.com/workmail/latest/userguide/troubleshooting.html) | 
| Amazon WorkSpaces | [Troubleshooting Amazon WorkSpaces Administration Issues](https://docs.aws.amazon.com/workspaces/latest/adminguide/admin_troubleshooting.html) \| [Troubleshooting Amazon WorkSpaces Client Issues](https://docs.aws.amazon.com/workspaces/latest/adminguide/client_troubleshooting.html) | 
| Amazon WorkSpaces Application Manager \(Amazon WAM\) | [Troubleshooting Amazon WAM Application Issues](http://docs.aws.amazon.com/wam/latest/userguide/troubleshooting.html) | 