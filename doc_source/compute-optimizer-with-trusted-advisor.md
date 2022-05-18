# Opt in AWS Compute Optimizer for Trusted Advisor checks<a name="compute-optimizer-with-trusted-advisor"></a>

Compute Optimizer is a service that analyzes the configuration and utilization metrics of your AWS resources\. This service reports whether your resources are correctly configured for efficiency and reliability\. It also suggests improvements you can implement to improve workload performance\. With Compute Optimizer, you view the same recommendations in your Trusted Advisor checks\.

You can opt in either your AWS account only, or all member accounts that are part of an organization in AWS Organizations\. For more information, see [Getting started](https://docs.aws.amazon.com/compute-optimizer/latest/ug/getting-started.html#account-opt-in) in the *AWS Compute Optimizer User Guide*\.

Once you opt in for Compute Optimizer, the following checks receive data from your Lambda functions and Amazon EBS volumes\. It can take up to 12 hours to generate the findings and optimization recommendations\. It can then take up to 48 hours to view your results in Trusted Advisor for the following checks:

[Cost optimization](cost-optimization-checks.md)
+ Amazon EBS over\-provisioned volumes
+ AWS Lambda over\-provisioned functions for memory size

[Performance](performance-checks.md)
+ Amazon EBS under\-provisioned volumes
+ AWS Lambda under\-provisioned functions for memory size

**Notes**  
Results for these checks are automatically refreshed several times daily\. Refresh requests are not allowed\. It might take a few hours for changes to appear\. Currently, you can’t exclude resources from these checks\.
Trusted Advisor already has the Underutilized Amazon EBS Volumes and the Overutilized Amazon EBS Magnetic Volumes checks\.   
Once you opt in with Compute Optimizer, we recommend that you use the new Amazon EBS over\-provisioned volumes and Amazon EBS under\-provisioned volumes checks instead\.

## Related information<a name="related-information-compute-optimizer"></a>

For more information, see the following topics:
+ [Viewing Amazon EBS volume recommendations](https://docs.aws.amazon.com/compute-optimizer/latest/ug/view-ebs-recommendations.html) in the *AWS Compute Optimizer User Guide* 
+ [Viewing Lambda function recommendations](https://docs.aws.amazon.com/compute-optimizer/latest/ug/view-lambda-recommendations.html) in the *AWS Compute Optimizer User Guide*
+ [Configuring Lambda function memory](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html#configuration-memory-console) in the *AWS Lambda Developer Guide*
+ [Request modifications to your Amazon EBS volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/requesting-ebs-volume-modifications.html) in the *Amazon EC2 User Guide for Linux Instances*