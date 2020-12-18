# Logging AWS Trusted Advisor console actions with AWS CloudTrail<a name="logging-using-cloudtrail-for-aws-trusted-advisor"></a>

Trusted Advisor is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Trusted Advisor\. CloudTrail captures actions for Trusted Advisor as events\. The calls captured include calls from the Trusted Advisor console\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon Simple Storage Service \(Amazon S3\) bucket, including events for Trusted Advisor\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine the request that was made to Trusted Advisor, the IP address from which the request was made, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, including how to configure and enable it, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## Trusted Advisor information in CloudTrail<a name="trusted-advisor-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in the Trusted Advisor console, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for Trusted Advisor, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

Trusted Advisor supports logging a subset of the Trusted Advisor console actions as events in CloudTrail log files\. CloudTrail logs the following actions:
+ `DescribeAccount`
+ `DescribeAccountAccess`
+ `DescribeChecks`
+ `DescribeCheckItems`
+ `DescribeCheckRefreshStatuses`
+ `DescribeCheckSummaries`
+ `DescribeNotificationPreferences`
+ `DescribeOrganization`
+ `DescribeOrganizationAccounts`
+ `DescribeReports`
+ `DescribeServiceMetadata`
+ `ExcludeCheckItems`
+ `GenerateReport`
+ `IncludeCheckItems`
+ `ListAccountsForParent`
+ `ListRoots`
+ `ListOrganizationalUnitsForParent`
+ `RefreshCheck`
+ `SetAccountAccess`
+ `SetOrganizationAccess`
+ `UpdateNotificationPreferences`

For a complete list of Trusted Advisor console actions, see [Trusted Advisor actions](security-trusted-advisor.md#trusted-advisor-operations)\.

**Note**  
CloudTrail also logs the Trusted Advisor API operations in the [AWS Support API Reference](https://docs.aws.amazon.com/awssupport/latest/APIReference/)\. For more information, see [Logging AWS Support API calls with AWS CloudTrail](logging-using-cloudtrail.md)\.

Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+ Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials\.
+ Whether the request was made with temporary security credentials for a role or federated user\.
+ Whether the request was made by another AWS service\.

For more information, see the [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

## Example: Trusted Advisor Log File Entries<a name="understanding-trusted-advisor-entries"></a>

 A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\.

**Example : Log entry for RefreshCheck**  
The following example shows a CloudTrail log entry that demonstrates the `RefreshCheck` action for the Amazon S3 Bucket Versioning check \(ID R365s2Qddf\)\.  

```
{
   "eventVersion":"1.04",
   "userIdentity":{
      "type":"IAMUser",
      "principalId":"AIDACKCEVSQ6C2EXAMPLE",
      "arn":"arn:aws:iam::123456789012:user/janedoe",
      "accountId":"123456789012",
      "accessKeyId":"AKIAIOSFODNN7EXAMPLE",
      "userName":"janedoe",
      "sessionContext":{
         "attributes":{
            "mfaAuthenticated":"false",
            "creationDate":"2020-10-21T22:06:18Z"
         }
      }
   },
   "eventTime":"2020-10-21T22:06:33Z",
   "eventSource":"trustedadvisor.amazonaws.com",
   "eventName":"RefreshCheck",
   "awsRegion":"us-east-1",
   "sourceIPAddress":"100.127.34.136",
   "userAgent":"AWS-TrustedAdvisor, aws-internal/3 aws-sdk-java/1.11.841 Linux/4.9.217-0.3.ac.206.84.332.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.262-b10 java/1.8.0_262 vendor/Oracle_Corporation",
   "requestParameters":{
      "checkId":"R365s2Qddf"
   },
   "responseElements":{
      "status":{
         "checkId":"R365s2Qddf",
         "status":"enqueued",
         "millisUntilNextRefreshable":3599993
      }
   },
   "requestID":"d23ec729-8995-494c-8054-dedeaEXAMPLE",
   "eventID":"a49d5202-560f-4a4e-b38a-02f1cEXAMPLE",
   "eventType":"AwsApiCall",
   "recipientAccountId":"123456789012"
}
```

**Example : Log entry for UpdateNotificationPreferences**  
The following example shows a CloudTrail log entry that demonstrates the `UpdateNotificationPreferences` action\.  

```
{
   "eventVersion":"1.04",
   "userIdentity":{
      "type":"IAMUser",
      "principalId":"AIDACKCEVSQ6C2EXAMPLE",
      "arn":"arn:aws:iam::123456789012:user/janedoe",
      "accountId":"123456789012",
      "accessKeyId":"AKIAIOSFODNN7EXAMPLE",
      "userName":"janedoe",
      "sessionContext":{
         "attributes":{
            "mfaAuthenticated":"false",
            "creationDate":"2020-10-21T22:06:18Z"
         }
      }
   },
   "eventTime":"2020-10-21T22:09:49Z",
   "eventSource":"trustedadvisor.amazonaws.com",
   "eventName":"UpdateNotificationPreferences",
   "awsRegion":"us-east-1",
   "sourceIPAddress":"100.127.34.167",
   "userAgent":"AWS-TrustedAdvisor, aws-internal/3 aws-sdk-java/1.11.841 Linux/4.9.217-0.3.ac.206.84.332.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.262-b10 java/1.8.0_262 vendor/Oracle_Corporation",
   "requestParameters":{
      "contacts":[
         {
            "id":"billing",
            "type":"email",
            "active":false
         },
         {
            "id":"operational",
            "type":"email",
            "active":false
         },
         {
            "id":"security",
            "type":"email",
            "active":false
         }
      ],
      "language":"en"
   },
   "responseElements":null,
   "requestID":"695295f3-c81c-486e-9404-fa148EXAMPLE",
   "eventID":"5f923d8c-d210-4037-bd32-997c6EXAMPLE",
   "eventType":"AwsApiCall",
   "recipientAccountId":"123456789012"
}
```

**Example : Log entry for GenerateReport**  
The following example shows a CloudTrail log entry that demonstrates the `GenerateReport` action\. This action creates a report for your AWS organization\.  

```
{
   "eventVersion":"1.04",
   "userIdentity":{
      "type":"IAMUser",
      "principalId":"AIDACKCEVSQ6C2EXAMPLE",
      "arn":"arn:aws:iam::123456789012:user/janedoe",
      "accountId":"123456789012",
      "accessKeyId":"AKIAIOSFODNN7EXAMPLE",
      "userName":"janedoe",
      "sessionContext":{
         "attributes":{
            "mfaAuthenticated":"false",
            "creationDate":"2020-11-03T13:03:10Z"
         }
      }
   },
   "eventTime":"2020-11-03T13:04:29Z",
   "eventSource":"trustedadvisor.amazonaws.com",
   "eventName":"GenerateReport",
   "awsRegion":"us-east-1",
   "sourceIPAddress":"100.127.36.171",
   "userAgent":"AWS-TrustedAdvisor, aws-internal/3 aws-sdk-java/1.11.864 Linux/4.9.217-0.3.ac.206.84.332.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.262-b10 java/1.8.0_262 vendor/Oracle_Corporation",
   "requestParameters":{
      "refresh":false,
      "includeSuppressedResources":false,
      "language":"en",
      "format":"JSON",
      "name":"organizational-view-report",
      "preference":{
         "accounts":[
            
         ],
         "organizationalUnitIds":[
            "r-j134"
         ],
         "preferenceName":"organizational-view-report",
         "format":"json",
         "language":"en"
      }
   },
   "responseElements":{
      "status":"ENQUEUED"
   },
   "requestID":"bb866dc1-60af-47fd-a660-21498EXAMPLE",
   "eventID":"2606c89d-c107-47bd-a7c6-ec92fEXAMPLE",
   "eventType":"AwsApiCall",
   "recipientAccountId":"123456789012"
}
```