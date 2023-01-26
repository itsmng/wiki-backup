# About Chat notification in ITSM-NG

This feature allows you to send chat notification from ITSM-NG to you chat application.

## Enable Chat notification

To activate chat notification, go to `Setup > Notifications`.

![](img/chat-notification/chat-notification_goto.png)

You need to enable followups to get notification on your chat application.
Set `Enable followup` and `Enable followups via chat` to `Yes` and then click on `Save`.

![](img/chat-notification/chat-notification_config_2.png)


## Third party followup configurations

Before manipulate notifications, you must configure an incoming webhook url which will get the notification for your chat application.

### Create incoming webhook with RocketChat

Connect to your RocketChat application with an administrator user.

Go to `Profile icon > Administration > Integrations > New`.

![](img/chat-notification/chat-notification_rocket_chat_webhook.png)

To configure your webhook, set a name and select the channel where notifications will be sent.

Set a user and save.

`Note: the selected user must be a bot.`

![](img/chat-notification/chat-notification_rocket_chat_webhook_2.png)

Then, click on your new webhook and copy the webhook URL : 

![](img/chat-notification/chat-notification_rocket_chat_webhook_3.png)


### Create incoming webhook with Slack

Connect to your Slack application with an administrator user.

Go to https://api.slack.com/ and click on `Your apps > Create an App > From scratch`.

![](img/chat-notification/chat-notification_slack_webhook.png)

![](img/chat-notification/chat-notification_slack_webhook_2.png)

Set a name, select the workspace and click on `Create App`.

Then, click on `Add features and functionality > Incoming Webhooks`.

![](img/chat-notification/chat-notification_slack_webhook_3.png)

Activate the feature, scroll down and click on `Add new Webhook to Workspace`.

![](img/chat-notification/chat-notification_slack_webhook_4.png)

Select the channel where notifications will be sent and click on `Allow`.

![](img/chat-notification/chat-notification_slack_webhook_5.png)

Copy the Webhook URL at the end of the page.

![](img/chat-notification/chat-notification_slack_webhook_6.png)


### Create incoming webhook with Teams

Connect to your Teams application with an administrator user.

Go to `More options > Connectors`

![](img/chat-notification/chat-notification_teams_webhook.png)

Find `Incoming Webhook` in the search bar and add the connector.

![](img/chat-notification/chat-notification_teams_webhook_2.png)

Click on the `Configure`, set a name to your webhook and click on `Create`.

![](img/chat-notification/chat-notification_teams_webhook_3.png)

Copy the webhook URL.

![](img/chat-notification/chat-notification_teams_webhook_4.png)


## Chat notification configurations

Go to `Setup > Notifications > Chat followups configuration`.

Select your chat application in the `Mode` dropdown and paste the webhook URL previously configured in `URL` field.

Click on `Save`.

![](img/chat-notification/chat-notification_rocket_chat_add_webhook.png)

To check that everything is working, click on `Test`. It will send a test notification on your chat application.

![](img/chat-notification/chat-notification_rocket_chat_add_webhook_2.png)

Sample test notification :

![](img/chat-notification/chat-notification_rocket_chat_add_webhook_3.png)

## How to implement a chat notification

`Note: for the following steps, we will take as an example the implementation of a chat notification when creating a new ticket`.

Go to `Setup > Notifications` and click on `Notifications`.

![](img/chat-notification/chat-notification_add_notification.png)

Search `Ticket` in the search filter and click on `New Ticket`.

Select the `Templates` tab and click on `Add a template`.

![](img/chat-notification/chat-notification_add_notification_4.png)

Select `Chat` option on the `Mode` dropdown and select the `Notification template` you want to associate it.

Click on `Add`.

![](img/chat-notification/chat-notification_add_notification_5.png)

## Enable automatic action to send the chat notification

Go to `Setup > Automatic actions`.

![](img/chat-notification/chat-notification_enable_automatic_action.png)

Search `Chat` in the search filter.

![](img/chat-notification/chat-notification_enable_automatic_action_2.png)

Click on `queuedchat` action and update the `Status` dropdown to `Scheduled`.

Update the `Run frequency` as you want and click on `Save`.

![](img/chat-notification/chat-notification_enable_automatic_action_3.png)

`Note: if you set Run mode as CLI, please refer to the following documentation: `[ITSM-NG Post installation](../post-install.md)
