# Monitoring and logging for AWS Trusted Advisor<a name="cloudwatch-ta"></a>

Monitoring is an important part of maintaining the reliability, availability, and performance of Trusted Advisor and your other AWS solutions\. AWS provides the following monitoring tools to watch Trusted Advisor, report when something is wrong, and take automatic actions when appropriate:
+ *Amazon EventBridge* delivers a near real\-time stream of system events that describe changes in AWS resources\. EventBridge enables automated event\-driven computing, as you can write rules that watch for certain events and trigger automated actions in other AWS services when these events happen\.

  For example, Trusted Advisor provides the **Amazon S3 Bucket Permissions** check\. This check identifies if you have buckets that have open access permissions or allow access to any authenticated AWS user\. If a bucket permission changes, the status changes for the Trusted Advisor check\. EventBridge detects this event and then sends you a notification so that you can take action\. For more information, see the [Amazon EventBridge User Guide](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)\.
+ AWS Trusted Advisor checks identify ways for you to reduce cost, increase performance, and improve security for your AWS account\. You can use EventBridge to monitor the status of Trusted Advisor checks\. You can then use Amazon CloudWatch to create alarms on Trusted Advisor metrics\. These alarms notify you when the status changes for a Trusted Advisor check, such as an updated resource or a service quota that is reached\.
+ *AWS CloudTrail* captures API calls and related events made by or on behalf of your AWS account and delivers the log files to an Amazon S3 bucket that you specify\. You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred\. For more information, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

**Topics**
+ [Monitoring AWS Trusted Advisor check results with Amazon EventBridge](cloudwatch-events-ta.md)
+ [Creating Amazon CloudWatch alarms to monitor AWS Trusted Advisor metrics](cloudwatch-metrics-ta.md)
+ [Logging AWS Trusted Advisor console actions with AWS CloudTrail](logging-using-cloudtrail-for-aws-trusted-advisor.md)