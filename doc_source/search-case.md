# Searching for support cases in Slack<a name="search-case"></a>

From your Slack channel, you can search for support cases from your AWS account and from other accounts that also configured the same channel and workspace\. For example, if your account \(123456789012\) and your coworker's account \(111122223333\) have configured the same workspace and channels in the AWS Support Center Console, you can use the AWS Support App to search and update each other's support cases\.

**To search for a support case**

1. In the Slack channel, enter the following command:

   `/awssupport search`

1. Specify the following options:

   1. For **AWS account**, choose the account to search\. This list only appears if you have multiple accounts in this channel\.

   1. For **Date range**, specify the date range to search for cases\.

   1. For **Case status**, choose the case status, such as **All open cases** or **Resolved**\.

      **Example : Search results**

      The following example returns two resolved support cases from one AWS account\.  
![\[View resolved support cases in Slack.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/search-case-results.png)

1. In the support case results, you can do the following:

   1. Choose **Share to channel** to share the search results with the channel\.

   1. Choose **Next 5 results** to see the next 5 cases\.

   1. Choose **See details** to see more information about a case\. You can choose **Show full message** to view the rest of the latest correspondence\.  
![\[View the returned support cases in Slack.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/search-case-results-see-details.png)