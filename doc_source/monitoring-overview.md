# Monitoring and logging for AWS Support<a name="monitoring-overview"></a>

Monitoring is an important part of maintaining the reliability, availability, and performance of AWS Support and your other AWS solutions\. AWS provides the following monitoring tools to watch AWS Support, report when something is wrong, and take automatic actions when appropriate:
+ *Amazon EventBridge* delivers a near real\-time stream of system events that describe changes in AWS resources\. EventBridge enables automated event\-driven computing, as you can write rules that watch for certain events and trigger automated actions in other AWS services when these events happen\. For more information, see the [Amazon EventBridge User Guide](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)\.
+ *AWS CloudTrail* captures API calls and related events made by or on behalf of your AWS account and delivers the log files to an Amazon S3 bucket that you specify\. You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred\. For more information, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

**Topics**
+ [Monitoring AWS Support cases with Amazon EventBridge](event-bridge-support.md)
+ [Logging AWS Support API calls with AWS CloudTrail](logging-using-cloudtrail.md)