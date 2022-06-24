# Home Assistant send notifications using AWS SNS


## 1. SETTING UP SNS WITHIN AWS

- Log into your AWS console and under “Security and Identity”, select “Identity & Access Management”.
- On the left-hand side, select “Users” then click “Create New Users”. Enter a name here and then click “Create”.
- You can either download the credentials or click the arrow to display them one time.

If you do not download them, you will lose them and will have to recreate a new user.

- Copy/Paste the two keys that are shown here in your `configuration.yaml` file.
- On the left-hand side of the screen go back to “Users” and select the user you just created. On the “Permissions” tab click the “Attach Policy” icon. Search for “SNS” and attach the policy “AmazonSNSFUullAccess”.
- Back to the AWS Console you now need to find “SNS” and click in to that service. It is under the Mobile Services group.
- On the left-hand side, select “Topics” then “Create new topic”.
- Choose a Topic Name and Display Name.
- Now check the box next to the Topic you just created and under Actions, select “Subscribe to topic”.
- In the box that pops up, select the Protocol = SMS and enter in the phone number next to “Endpoint” you wish to SMS. Now click “Create”. Note: Changing the protocol creates other types of notification, such as SMTP.
- Repeat for additional numbers.
- Back in the “Users” section you will see a long alphanumeric line that starts with “arn:” and ends with the Topic Name you choose previously. This is what your “**target**” in Home Assistant will be.

## 2. CONFIGURING HOME ASSISTANT TO SEND AWS SNS NOTIFICATIONS

Add the lines in the configuration.yaml file from this repository to your configuration.yaml file

## 3. TEST

![Untitled](https://user-images.githubusercontent.com/45504305/175666351-17ae6ab6-8bf1-418f-990a-cdb38f5ee5f7.png)

- Go to Developer Tools, YAML
- Click Check Configuration
- Click Restart and wait for HA to restart

![Untitled (1)](https://user-images.githubusercontent.com/45504305/175666398-febeb28d-a2be-4f4a-a4c5-1ca36907ac04.png)

- Still in Developer Tools, click on “Services”
- Select the new notification service “sns_us_east_1”
- In “Target”, use the topic name from AWS SNS
