# Monitoring AWS Support cases with Amazon EventBridge<a name="event-bridge-support"></a>

You can use Amazon EventBridge to detect and react to changes for your AWS Support cases\. Then, based on the rules that you create, EventBridge invokes one or more target actions when an event matches the values that you specify in a rule\. 

Depending on the event, you can send notifications, capture event information, take corrective action, initiate events, or take other actions\. For example, you can get notified whenever the following actions occur in your account:
+ Create a support case
+ Add a case correspondence to an existing support case
+ Resolve a support case
+ Reopen a support case

**Note**  
AWS Support delivers events on a best effort basis\. Events are not always guaranteed to be delivered to EventBridge\.

## Creating an EventBridge rule for AWS Support cases<a name="creating-event-bridge-events-rule-for-aws-support"></a>

You can create an EventBridge rule to get notified for AWS Support case events\. The rule will monitor updates for support cases in your account, including actions that you, your IAM users, or support agents perform\. Before you create a rule for AWS Support case events, do the following:
+ Familiarize yourself with events, rules, and targets in EventBridge\. For more information, see [What is Amazon EventBridge?](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html) in the *Amazon EventBridge User Guide*\.
+ Create the target to use in your event rule\. For example, you can create an Amazon Simple Notification Service \(Amazon SNS\) topic so that whenever a support case is updated, you will receive a text message or email\. For more information, see [EventBridge targets](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-targets.html)\.

**Note**  
AWS Support is a global service and doesn't use separate Regions\. To receive updates for your support cases, use the US East \(N\. Virginia\) Region\.

**To create an EventBridge rule for AWS Support case events**

1. Open the Amazon EventBridge console at [https://console\.aws\.amazon\.com/events/](https://console.aws.amazon.com/events/)\.

1. If you haven't already, use the **Region selector** in the upper\-right corner of the page and choose **US East \(N\. Virginia\)**\.

1. In the navigation pane, choose **Rules**\.

1. Choose **Create rule**\.

1. On the **Define rule detail** page, enter a name and description for your rule\.

1. Keep the default values for **Event bus** and **Rule type**, and then choose **Next**\.

1. On the **Build event pattern** page, for **Event source**, choose **AWS events or EventBridge partner events**\.

1. Under **Event pattern**, keep the default value for **AWS services**\.

1. For **AWS service**, choose **Support**\.

1. For **Event type**, choose **Support Case Update**\.<a name="choose-service-category"></a>

1. Choose **Next**\.

1. In the **Select target\(s\)** section, choose the target that you created for this rule, and then configure any additional options that are required for that type\. For example, if you choose Amazon SNS, make sure that your SNS topic is configured correctly so that you will be notified by email or SMS\.

1. Choose **Next**\.

1. \(Optional\) On the **Configure tags** page, add any tags and then choose **Next**\.

1. On the **Review and create** page, review your rule setup and ensure that it meets your event monitoring requirements\.

1. Choose **Create rule**\. Your rule will now monitor for AWS Support case events and then send them to the target that you specified\.

**Notes**  
When you receive an event, you can use the `origin` parameter to determine whether you or an AWS Support agent added a case correspondence to a support case\. The value for `origin` can be either `CUSTOMER` or `AWS`\.   
Currently, only events for the `AddCommunicationToCase` action will have this value\.
For more information about creating event patterns, see [Event patterns](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html) in the *Amazon EventBridge User Guide*\.
You can also create another rule for the **AWS API Call via CloudTrail** event type\. This rule will monitor AWS CloudTrail logs for AWS Support API calls in your account\.

## Example AWS Support events<a name="example-event-logs-for-support-cases"></a>

The following events are created when support actions occur in your account\.

**Example : Create support case**  
The following event is created when a support case is created\.  

```
{
    "version": "0",
    "id": "3433df007-9285-55a3-f6d1-536944be45d7",
    "detail-type": "Support Case Update",
    "source": "aws.support",
    "account": "111122223333",
    "time": "2022-02-21T15:51:19Z",
    "region": "us-east-1",
    "resources": [],
    "detail": {
        "case-id": "case-111122223333-muen-2022-7118885805350839",
        "display-id": "1234563851",
        "communication-id": "",
        "event-name": "CreateCase",
        "origin": ""
    }
}
```

**Example : Update support case**  
The following event is created when AWS Support replies to a support case\.  

```
{
    "version": "0",
    "id": "f90cb8cb-32be-1c91-c0ba-d50b4ca5e51b",
    "detail-type": "Support Case Update",
    "source": "aws.support",
    "account": "111122223333",
    "time": "2022-02-21T15:51:31Z",
    "region": "us-east-1",
    "resources": [],
    "detail": {
        "case-id": "case-111122223333-muen-2022-7118885805350839",
        "display-id": "1234563851",
        "communication-id": "ekko:us-east-1:12345678-268a-424b-be08-54613cab84d2",
        "event-name": "AddCommunicationToCase",
        "origin": "AWS"
    }
}
```

**Example : Resolve support case**  
The following event is created when a support case is resolved\.  

```
{
    "version": "0",
    "id": "1aa4458d-556f-732e-ddc1-4a5b2fbd14a5",
    "detail-type": "Support Case Update",
    "source": "aws.support",
    "account": "111122223333",
    "time": "2022-02-21T15:51:31Z",
    "region": "us-east-1",
    "resources": [],
    "detail": {
        "case-id": "case-111122223333-muen-2022-7118885805350839",
        "display-id": "1234563851",
        "communication-id": "",
        "event-name": "ResolveCase",
        "origin": ""
    }
}
```

**Example : Reopen support case**  
The following event is created when a support case is reopened\.  

```
{
    "version": "0",
    "id": "3bb9d8fe-6089-ad27-9508-804209b233ad",
    "detail-type": "Support Case Update",
    "source": "aws.support",
    "account": "111122223333",
    "time": "2022-02-21T15:47:19Z",
    "region": "us-east-1",
    "resources": [],
    "detail": {
        "case-id": "case-111122223333-muen-2021-27f40618fe0303ea",
        "display-id": "1234563851",
        "communication-id": "",
        "event-name": "ReopenCase",
        "origin": ""
    }
}
```