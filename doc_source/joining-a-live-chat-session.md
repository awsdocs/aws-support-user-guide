# Joining a live chat session with AWS Support<a name="joining-a-live-chat-session"></a>

When you request a live chat option for your case, the AWS Support App creates a chat channel for you and the AWS Support agent\. Use this chat channel to communicate with the support agent and any others that you invited to the live chat\.

**Important**  
Anyone who joins your live chat channel can view details about this specific support case\. We recommend that you only add users that require access to your support cases\.

**To join a live chat session with AWS Support**

1. In the Slack application, navigate to the channel that the AWS Support App creates for you\. The channel name includes your support case ID, such as *awscase\-1234567890*\.
**Note**  
The AWS Support App adds a pinned message to the live chat channel that contains details about your support case\. From the pinned message, you can end the chat or resolve the case\. You can find all pinned messages in this channel under the channel name\.

1. When the support agent joins the channel, you can chat about your support case\. Until a support agent joins the channel, the agent won't see messages in that chat, and the messages won't appear in your case correspondence\.  
![\[Screenshot of how to create a live chat in Slack.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/pending-open-case-in-channel.png)

1. \(Optional\) Add other members to the chat channel\. By default, chat channels are private\.

1. After the support agent joins the chat, the chat channel is active and the AWS Support App records the chat\. 

   You can chat with the agent about your support case and upload any file attachments to the channel\. The AWS Support App automatically saves your files and chat log to your case correspondence\.
**Note**  
When you chat with a support agent, note the following differences in Slack for the AWS Support App:  
Support agents can't view shared messages or threads\. To share text from a message or thread, enter the text as a new message\.
If you edit or delete a message, the agent still sees the original message\. You must enter your new message again to show the revision\.  
**Example : Live chat session**  

   The following is an example of a live chat session with a support agent to fix a connectivity issue for two Amazon Elastic Compute Cloud \(Amazon EC2\) instances\.  
![\[Chat window with a live support agent in the Slack channel.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/live-chat-slack-channel.png)

1. \(Optional\) To stop the live chat, choose **End chat**\. The support agent leaves the channel and the AWS Support App stops recording the live chat\. You can find the chat history attached to the case correspondence for this support case\.

1. If the issue is resolved, you can choose **Resolve case** from the pinned message or enter `/awssupport resolve`\.  
**Example : End a live chat**  

   The following pinned message shows the case details about an Amazon EC2 instance\. You can find the pinned messages under the Slack channel name\.  
![\[End a chat or resolve a support case in the Slack channel.\]](http://docs.aws.amazon.com/awssupport/latest/user/images/supportapp/resolve-end-chat-slack-channel.png)