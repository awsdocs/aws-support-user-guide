# About the AWS Support API<a name="Welcome"></a>

The AWS Support API provides access to some of the features of the [AWS Support Center](https://console.aws.amazon.com/support/home#/)\. AWS provides this access for [AWS Support](https://aws.amazon.com/premiumsupport/) customers who have a Business or Enterprise support plan\. The service currently provides two different groups of operations:

+ [Support Case Management](#casemanagement) operations to manage the entire life cycle of your AWS support cases, from creating a case to resolving it\. 

+ [Trusted Advisor](#trustedadvisorsection) operations to access the checks provided by [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/trustedadvisor/)\. 

For information about the operations and data types provided by AWS Support, see the [AWS Support API Reference](http://docs.aws.amazon.com/awssupport/latest/APIReference/)\. 


+ [Support Case Management](#casemanagement)
+ [Trusted Advisor](#trustedadvisorsection)
+ [Endpoint](#endpoint)
+ [Support in AWS SDKs](#sdksupport)

## Support Case Management<a name="casemanagement"></a>

Using the operations for support case management, you can perform these tasks:

+ Open a support case\. 

+ Get a list and detailed information about recent support cases\. 

+ Narrow your search for support cases by dates and case identifiers, including cases that have been resolved\. 

+ Add communications and file attachments to your cases, and add email recipients for case correspondence\. 

+ Resolve your cases\. 

The AWS Support API supports CloudTrail logging for support case management operations\. For more information, see [Logging AWS Support API Calls with AWS CloudTrail](logging-using-cloudtrail.md)\.

For example Java code that demonstrates how to manage the entire life cycle of an AWS Support case, see [Programming the Life of an AWS Support Case](Case_Life_Cycle.md)\. 

## Trusted Advisor<a name="trustedadvisorsection"></a>

Using the Trusted Advisor operations, you can perform these tasks:

+ Get names and identifiers for the checks that Trusted Advisor offers\.

+ Request that a Trusted Advisor check be run against your account and resources\. 

+ Obtain summaries and detailed information for your Trusted Advisor checks\. 

+ Request that Trusted Advisor checks be refreshed\. 

+ Obtain the status of each Trusted Advisor check you have requested\. 

The AWS Support API supports CloudWatch Events for Trusted Advisor operations\. For more information, see [Monitoring Trusted Advisor Check Results with Amazon CloudWatch Events](cloudwatch-events-ta.md)\.

For an example that uses the Trusted Advisor operations, see [Using Trusted Advisor as a Web Service](trustedadvisor.md)\. 

## Endpoint<a name="endpoint"></a>

Use this endpoint to access AWS Support:

+ https://support\.us\-east\-1\.amazonaws\.com

**Warning**  
The AWS Support endpoint creates cases in the production database\. Include a subject line such as "TEST CASE\-\-Please ignore" when you call `[CreateCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html)` for testing, and close the test cases you create by calling `[ResolveCase](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html)`\. 

For additional information about using AWS endpoints, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

## Support in AWS SDKs<a name="sdksupport"></a>

The AWS Command Line Interface, the AWS Tools for Windows PowerShell, and the AWS Software Development Kits \(SDKs\) include support for the AWS Support API:

+ [AWS CLI](http://docs.aws.amazon.com/cli/latest/reference/support/index.html)

+ [AWS Tools for Windows PowerShell](http://docs.aws.amazon.com/powershell/latest/reference/items/AWS_Support_API_cmdlets.html)

+ [AWS SDK for Java](http://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/index.html?com/amazonaws/services/support/AWSSupport.html)

+ [AWS SDK for JavaScript](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/Support.html)

+ [AWS SDK for \.NET](http://docs.aws.amazon.com/sdkfornet/v3/apidocs/items/AWSSupport/NAWSSupport.html)

+ [AWS SDK for PHP](http://docs.aws.amazon.com/aws-sdk-php/v3/api/api-support-2013-04-15.html)

+ [AWS SDK for Python \(Boto\)](http://boto.readthedocs.org/en/latest/support_tut.html)

+ [AWS SDK for Ruby](http://docs.aws.amazon.com/sdkforruby/api/Aws/Support.html)