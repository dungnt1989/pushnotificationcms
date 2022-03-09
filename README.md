
### Description:
This is a simple notifications module, completely developed using Mendix components. A developer can directly add **SUB_CreateNotification** microflow into their own microflow, to send a notification to the user. Things like redirecting to required context page can also be done when on click of the notification. 

### Features:
1.	Get push notifications with simple configuration.
2.	User has the access to make the notification as read.
3.	A click on the notification will redirect to that particular context page, with a simple customization.
4.	Administration user can configure the notification Subject and Message using **MessageTemplateConfig** page.

### Configuration: 
1.	Download **MxModelReflection** from appstore, as it is dependency module to synchronize the entities.
2.	Add **MxObjectOverview** page into the navigation with Administration rights. 
3.	Add **MessageTemplateConfig** page into the navigation giving only administration access to it.
Administrator can add multiple templates based on requirement and set `Subject`, `Message` of the notification. Dynamic values can also be set using tokens.
4.	Add **CurrentUser_Snippet** from **USE_ME** folder in your layouts.
5.	Call **SUB_CreateNotification** microflow when needed to generate a notification in your microflow.
6.	Retrieve MessageTemplate object with some valid name and add Subject, Message and CurrentDateTime to SUB_CreateNotificaiton microflow parameters.
7.	Also add **SUB_ReplaceNotificationToken** microflow, and required parameters to it, to get the dynamic values from tokens.
8.	Now retrieve the account from **Administrator.Account** entity to whom the notification has to be sent and map to **SentTo** parameter.
9.	Similarly, retrieve the account from whom the notification being sent and map to **SentFrom** parameter.
10.	For redirecting to a page on click of notification, you can use the noitification category enumeration.
11.	For example, if the user needs to send a notification for a policy approval, we can create a new enumeration value (like PolicyApproval). Create an association from notification entity to that particular entity (to which page it has to get redirected). Now use **ACT_GoToSource** microflow for an onclick. You can use the exclusive split and divide the paths using enumeration values, retrieve the entity which is been associated while creating a notification object, now show page  pass the entity which is been retrieved. 
12.	After running the application, login with Admin, navigate to MxObject_Overview page and sync all the necessary entities to select them in the MessageTemplate configuration as tokens.
13.	Now navigate to Message template configuration, create new template with some valid name, given while retrieving  MessageTemplate object in step 6.
14.	Select the Message template and create new tokens for the MessageTemplate, to get the dynamic values. Copy the token names and add them in the Subject or Message along with the string. Eg. `Subject: Need approval for policy no {%PolicyNo%}, sent from {%Agent%}`. 


