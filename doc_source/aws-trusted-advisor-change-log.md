# Change log for AWS Trusted Advisor checks<a name="aws-trusted-advisor-change-log"></a>

See the following topic for recent changes to Trusted Advisor checks\. 

For more information about the available checks, see the [AWS Trusted Advisor best practice checklist](http://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practice-checklist/)\.

## Trusted Advisor check removal<a name="trusted-advisor-checks-removal"></a>

**Note**  
Trusted Advisor removed the following checks on November 18, 2020\.


****  

| Checks removed on November 18, 2020 | Check category | Check ID | 
| --- | --- | --- | 
|  EC2Config Service for EC2 Windows Instances  | Fault Tolerance |  V77iOLlBqz  | 
|  ENA Driver Version for EC2 Windows Instances  | Fault Tolerance |  TyfdMXG69d  | 
|  NVMe Driver Version for EC2 Windows Instances  | Fault Tolerance |  yHAGQJV9K5  | 
|  PV Driver Version for EC2 Windows Instances  | Fault Tolerance |  Wnwm9Il5bG  | 
|  EBS Active Volumes  | Service Limits |  fH7LL0l7J9  | 

If you use results from all checks in the Trusted Advisor console or the AWS Support API, these checks won't appear in check results\. If you use any of these five checks such as specifying the check ID in an AWS Support API operation or your code, you will need to remove these checks to avoid API call errors\.

Amazon Elastic Block Store no longer has a limit on the number of volumes that you can provision\.

You can monitor your Amazon EC2 instances and ensure they are up\-to\-date by using [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html), other third\-party tools, or write your own scripts to return driver information for Windows Management Instrumentation \(WMI\)\.