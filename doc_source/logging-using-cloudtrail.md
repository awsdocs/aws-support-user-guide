# Logging AWS Support API Calls with AWS CloudTrail<a name="logging-using-cloudtrail"></a>

AWS Support is integrated with CloudTrail, a service that captures specific API calls and delivers log files to an Amazon S3 bucket that you specify\. CloudTrail captures API calls made from the AWS Support console or from your code to the AWS Support APIs\. With the information collected by CloudTrail, you can determine the request that was made to AWS Support, the IP address from which the request was made, who made the request, when it was made, and so on\. 

To learn more about CloudTrail, including how to configure and enable it, see the [AWS CloudTrail User Guide](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## AWS Support Information in CloudTrail History<a name="aws-support-info-in-cloudtrail-history"></a>

The CloudTrail API activity history feature lets you look up and filter events captured by CloudTrail\. You can look up events related to the creation, modification, or resolution of support cases in your AWS account\. Events can be looked up by using the CloudTrail console, or programmatically by using the AWS SDKs or AWS CLI \([lookup\-events](http://docs.aws.amazon.com/cli/latest/reference/cloudtrail/lookup-events.html)\)\. 

The following actions are supported:

+ [AddAttachmentsToSet](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddAttachmentsToSet.html)

+ [AddCommunicationToCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddCommunicationToCase.html)

+ [CreateCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html)

+ [ResolveCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html)

## AWS Support Information in CloudTrail Logging<a name="aws-support-info-in-cloudtrail-logging"></a>

When CloudTrail logging is enabled in your AWS account, API calls made to specific AWS Support actions are tracked in CloudTrail log files\. AWS Support actions are written with other AWS service records\. CloudTrail determines when to create and write to a new file based on a time period and file size\.

The following actions are supported:

+ [AddAttachmentsToSet](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddAttachmentsToSet.html)

+ [AddCommunicationToCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddCommunicationToCase.html)

+ [CreateCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html)

+ [DescribeAttachment](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeAttachment.html)

+ [DescribeCases](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCases.html)

+ [DescribeCommunications](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCommunications.html)

+ [DescribeServices](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeServices.html)

+ [DescribeSeverityLevels](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeSeverityLevels.html)

+ [ResolveCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html)

Every log entry contains information about who generated the request\. The user identity information in the log entry helps you determine the following: 

+ Whether the request was made with root or IAM user credentials

+ Whether the request was made with temporary security credentials for a role or federated user

+ Whether the request was made by another AWS service

For more information, see the [CloudTrail userIdentity Element](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

You can store your log files in your Amazon S3 bucket for as long as you want, but you can also define Amazon S3 lifecycle rules to archive or delete log files automatically\. By default, your log files are encrypted with Amazon S3 server\-side encryption \(SSE\)\.

If you want to be notified upon log file delivery, you can configure CloudTrail to publish Amazon SNS notifications when new log files are delivered\. For more information, see [Configuring Amazon SNS Notifications for CloudTrail](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)\.

You can also aggregate AWS Support log files from multiple AWS regions and multiple AWS accounts into a single Amazon S3 bucket\. 

For more information, see [Receiving CloudTrail Log Files from Multiple Regions](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html) and [Receiving CloudTrail Log Files from Multiple Accounts](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)\.

## Understanding AWS Support Log File Entries<a name="understanding-aws-support-entries"></a>

CloudTrail log files contain one or more log entries\. Each entry lists multiple JSON\-formatted events\. A log entry represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. The log entries are not an ordered stack trace of the public API calls, so they do not appear in any specific order\.

The following example shows a CloudTrail log entry that demonstrates the [CreateCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html) action\.

```
{
   "Records": [
      {
         "eventVersion": "1.04",
         "userIdentity": {
            "type": "IAMUser",
            "principalId": "AIDACKCEVSQ6C2EXAMPLE",
            "arn": "arn:aws:iam::111122223333:user/janedoe",
            "accountId": "111122223333",
            "accessKeyId": "AKIAIOSFODNN7EXAMPLE",
            "userName": "janedoe",
            "sessionContext": {
               "attributes": {
                  "mfaAuthenticated": "false",
                  "creationDate": "2016-04-13T17:51:37Z"
               }
            },
            "invokedBy": "signin.amazonaws.com"
         },
         "eventTime": "2016-04-13T18:05:53Z",
         "eventSource": "support.amazonaws.com",
         "eventName": "CreateCase",
         "awsRegion": "us-east-1",
         "sourceIPAddress": "198.51.100.15",
         "userAgent": "signin.amazonaws.com",
         "requestParameters": {
            "severityCode": "low",
            "categoryCode": "other",
            "language": "en",
            "serviceCode": "support-api",
            "issueType": "technical"
         },
         "responseElements": {
            "caseId": "case-111122223333-muen-2016-c3f2077e504940f2"
         },
         "requestID": "58c257ef-01a2-11e6-be2a-01c031063738",
         "eventID": "5aa34bfc-ad5b-4fb1-8a55-2277c86e746a",
         "eventType": "AwsApiCall",
         "recipientAccountId": "111122223333"
      }
   ],
   ...
}
```