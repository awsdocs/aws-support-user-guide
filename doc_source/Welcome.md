# About the AWS Support API<a name="Welcome"></a>

The AWS Support API provides access to some of the features in the [AWS Support Center](https://console.aws.amazon.com/support)\. 

The API provides two different groups of operations:
+ [Support case management](#casemanagement) operations to manage the entire life cycle of your AWS support cases, from creating a case to resolving it
+ [Trusted Advisor](#trustedadvisorsection) operations to access [AWS Trusted Advisor](trusted-advisor.md) checks

**Note**  
You must have a Business or Enterprise Support plan to use the AWS Support API\. For more information, see [AWS Support](http://aws.amazon.com/premiumsupport)\.

For more information about the operations and data types provided by AWS Support, see the [AWS Support API Reference](https://docs.aws.amazon.com/awssupport/latest/APIReference/)\.

**Topics**
+ [Support case management](#casemanagement)
+ [Trusted Advisor](#trustedadvisorsection)
+ [Endpoint](#endpoint)
+ [Support in AWS SDKs](#sdksupport)

## Support case management<a name="casemanagement"></a>

You can use the API to perform the following tasks:
+ Open a support case
+ Get a list and detailed information about recent support cases
+ Filter your search for support cases by dates and case identifiers, including resolved cases
+ Add communications and file attachments to your cases, and add the email recipients for case correspondences
+ Resolve your cases

The AWS Support API supports CloudTrail logging for support case management operations\. For more information, see [Logging AWS Support API calls with AWS CloudTrail](logging-using-cloudtrail.md)\.

For example Java code that demonstrates how to manage the entire life cycle of a support case, see [Programming an AWS Support case](Case_Life_Cycle.md)\. 

## Trusted Advisor<a name="trustedadvisorsection"></a>

You can use the Trusted Advisor operations to perform the following tasks:
+ Get the names and identifiers for the Trusted Advisor checks
+ Request that a Trusted Advisor check be run against your AWS account and resources
+ Get summaries and detailed information for your Trusted Advisor check results
+ Refresh your Trusted Advisor checks
+ Get the status of each Trusted Advisor check

The AWS Support API supports CloudTrail logging for Trusted Advisor operations\. For more information, see [AWS Trusted Advisor information in CloudTrail logging](logging-using-cloudtrail.md#cloudtrail-logging-for-trusted-advisor)\.

You can use Amazon CloudWatch Events to monitor for changes to your check results for Trusted Advisor\. For more information, see [Monitoring Trusted Advisor check results with Amazon CloudWatch Events](cloudwatch-events-ta.md)\.

For example Java code that demonstrates how to use the Trusted Advisor operations, see [Using Trusted Advisor as a web service](trustedadvisor.md)\.

## Endpoint<a name="endpoint"></a>

You can use the following endpoint to access the AWS Support API:
+ https://support\.us\-east\-1\.amazonaws\.com

**Important**  
The AWS Support endpoint creates cases in the production database\. If you're creating test support cases, we recommend that you include a subject line, such as **TEST CASE\-Please ignore**, when you call the [CreateCase](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html) operation\. After you're done testing, call the [ResolveCase](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html) operation to resolve the case\.

For more information about using AWS endpoints, see [Regions and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

## Support in AWS SDKs<a name="sdksupport"></a>

The AWS Command Line Interface \(AWS CLI\), and the AWS Software Development Kits \(SDKs\) include support for the AWS Support API\.

For a list of languages that support the AWS Support API, choose an operation name, such as [CreateCase](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html), and in the [See Also](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html#API_CreateCase_SeeAlso) section, choose your preferred language\.