# Using Trusted Advisor as a Web Service<a name="trustedadvisor"></a>

The AWS Support service enables you to write applications that interact with [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/trustedadvisor/)\. This topic shows you how to get a list of Trusted Advisor checks, refresh one of them, and obtain the detailed results from the check\. These tasks are demonstrated in Java\. For information about support for other languages, see [Tools for Amazon Web Services](http://aws.amazon.com/tools/)\. 


+ [Get the List of Available Trusted Advisor Checks](#Get_TA_Checks)
+ [Request a Trusted Advisor Check Result](#requestcheck)
+ [Poll a Trusted Advisor Check for Status Changes](#getcheckstatus)
+ [Print Details of a Trusted Advisor Check](#printdetails)

## Get the List of Available Trusted Advisor Checks<a name="Get_TA_Checks"></a>

The following Java code snippet creates an instance of an AWS Support client that you can use to call all Trusted Advisor actions\. Next, the code gets the list of Trusted Advisor checks and their corresponding `CheckId` values by calling the `[DescribeTrustedAdvisorChecks](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorChecks.html)` action\. You can use this information to build user interfaces that enable users to select the check they want to run or refresh\. 

```
private static AWSSupportClient createClient()
{
    AWSSupportClient client = new AWSSupportClient(); 
    client.setEndpoint("https://support.us-east-1.amazonaws.com");
    return client;
}

public static void getTaChecks(AWSSupportClient client)
{
    DescribeTrustedAdvisorChecksResult result = 
        client.describeTrustedAdvisorChecks(
            new DescribeTrustedAdvisorChecksRequest()
                .withLanguage("en"));
                         
    for (TrustedAdvisorCheckDescription checkDescription : 
        result.getChecks())
    {
        System.out.println(checkDescription.getId());
        System.out.println(checkDescription.getName()); 
    }
```

## Request a Trusted Advisor Check Result<a name="requestcheck"></a>

After you have selected the check you want to run, you submit a request by using the `[DescribeTrustedAdvisorCheckResult](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckResult.html)` action\. 

The following Java code snippet uses the `DescribeTrustedAdvisorChecksResult` instance referenced by the variable `result`, which was obtained in the preceding code snippet\. Rather than defining a check interactively through a user interface, the snippet simply submits a request for the first check in the list to be run by specifying an index value of 0 in each `result.getChecks().get(0)` call\. Next, the code defines an instance of `DescribeTrustedAdvisorCheckResultRequest`, which it passes to an instance of `DescribeTrustedAdvisorCheckResultResult` called `checkResult`\. You can use the member structures of this data type to view the results of the check\. 

```
    final String checkId = result.getChecks().get(0).getId();
    final String checkName = result.getChecks().get(0).getName(); 

    System.out.println("The following check is being refreshed: " + 
        checkId + ":" + "  " + checkName);
            
    DescribeTrustedAdvisorCheckResultRequest checkResultRequest = 
        new DescribeTrustedAdvisorCheckResultRequest().withCheckId(checkId);
    DescribeTrustedAdvisorCheckResultResult checkResult = 
        client.describeTrustedAdvisorCheckResult(checkResultRequest);
```

## Poll a Trusted Advisor Check for Status Changes<a name="getcheckstatus"></a>

After you have submitted the request to run a Trusted Advisor check, you use the `[DescribeTrustedAdvisorCheckRefreshStatuses](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckRefreshStatuses.html)` action to request the status of a check that you've started\. 

The following Java code snippet gets the status of the check requested in the following section, using the value corresponding in the `CheckId` variable\. In addition, the code demonstrates several other uses of the Trusted Advisor service:

1. You can call `getMillisUntilNextRefreshable` by traversing the objects contained in the `DescribeTrustedAdvisorCheckRefreshStatusesResult` instance\. You can use the value returned to test whether you want your code to proceed with refreshing the check\. 

1. If `timeUntilRefreshable` equals zero, you can request a refresh of the check\. 

1. Using the status returned, you can continue to poll for status changes; the code snippet sets the polling interval to a recommended ten seconds\. If the status is either `enqueued` or `in_progress`, the loop returns and requests another status\. If the call returns `successful`, the loop terminates\. 

1.  Last, the code returns an instance of a `DescribeTrustedAdvisorCheckResultResult` data type that you can use to traverse the information produced by the check\. 

```
    String status = "";
            
    do 
    {
        DescribeTrustedAdvisorCheckRefreshStatusesResult 
            describeStatusResult = 
                client.describeTrustedAdvisorCheckRefreshStatuses(
                    new DescribeTrustedAdvisorCheckRefreshStatusesRequest()
                    .withCheckIds(java.util.Arrays.asList(checkId)));
        final long timeUntilRefreshable = 
            describeStatusResult.getStatuses().get(0)
            .getMillisUntilNextRefreshable();

        if (timeUntilRefreshable != 0) 
        {
            System.out.println(
                "Can't refresh; check was recently refreshed. "
                + "Time until refreshable: "
                + timeUntilRefreshable);
        }

        DescribeTrustedAdvisorCheckRefreshStatusesResult 
            describeRefreshStatusResult = 
                client.describeTrustedAdvisorCheckRefreshStatuses(
                    new DescribeTrustedAdvisorCheckRefreshStatusesRequest()
                    .withCheckIds(java.util.Arrays.asList(checkId)));

        status = describeRefreshStatusResult.getStatuses().get(0).getStatus();
            
        System.out.println("Check status: " + status.toString()); 
            
        try 
        {
            Thread.sleep(10000);
        } 
        catch (InterruptedException e) 
        {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }

        // Fetch the updated result.
        DescribeTrustedAdvisorCheckResultResult result1 = 
            client.describeTrustedAdvisorCheckResult(
                new DescribeTrustedAdvisorCheckResultRequest()
                .withCheckId(checkId));
           
        return result1;    
    }
    while (status.equals("enqueued") || status.equals("in_progress"));
```

## Print Details of a Trusted Advisor Check<a name="printdetails"></a>

The following Java code snippet iterates over the `DescribeTrustedAdvisorCheckResultResult` instance returned in the previous section to get a list of resources flagged by the Trusted Advisor check\. 

```
    // Print ResourceIds for flagged resources. 
    for (TrustedAdvisorResourceDetail flaggedResource : 
        result1.getResult().getFlaggedResources())
    {
        System.out.println(
            "The resource for this ResourceID has been flagged: " + 
            flaggedResource.getResourceId());
    }
```