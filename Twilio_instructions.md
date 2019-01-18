Twilio integration for Ethicsware
=======================================

![imgs/sms_example.jpg](imgs/sms_example.jpg)

This lets you use your ethicsware project over text message, so you can text back and forth with a number!

This uses the Twilio API. 

(As a note, this API costs $. There is a free trial. 
It is relatively inexpensive - $1/month for a phone number, and $0.0047 to send and receive one text message. So if you send and receive 100 text messages/mo, it will cost $1.47/mo.)

## How this works

Twilio is an API that helps us respond to SMS (text) messages. Through Twilio, we can rent a specific phone number and use it for our own usage. Let's say that phone number is `+1-(212)-555-1234`.

Twilio has the ability to define "incoming webhooks". This means: every time `+1-(212)-555-1234` receives a text message from somebody, Twilio will trigger an HTTP request with the text message as arguments.

This code creates a web server that receives this requests and processes it to find the text message that was sent. 

Then, this webserver, using our code, will create a response to the text message, and send it back.

## Step-by-step instructions for SMS setup:

### Glitch:
#### 1. Create an account
Go to https://glitch.com.
#### 2. Remix (Copy) [this glitch example](https://glitch.com/edit/#!/magnificent-class)
![remix_screenshot](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/glitch_1_remix.png)
#### 3. Preview/test
You should now have a new URL, like `superb-owl.glitch.com`, or such. Click on `show` (with the glasses) to preview it!
![remix_screenshot](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/glitch_2_show.png)

### Twilio:
#### 1. Sign up for an account
#### 2. Start a project at this URL: https://www.twilio.com/console/projects/create
(Make sure you start a 'Programmable SMS' project.)
#### 3. Buy a phone number
After creating a project, buy a phone number at [this link](https://www.twilio.com/console/phone-numbers/search).
  - Search for a number that has SMS enabled, and click buy.
  ![imgs/twilio_2_search](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/twilio_2_search.png)
  ![imgs/twilio_3_buy](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/twilio_3_buy.png)
  Great! Now your number should be linked with your project.
#### 4. Set the incoming webhook
  - Go to this page to set the incoming webhook: https://www.twilio.com/console/phone-numbers/incoming
  - Click on your phone number:
  ![imgs/twilio_4_clicknumber](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/twilio_4_clicknumber.png)
  - And set the webhook and hit save.
  ![imgs/twilio_5_setwebhook](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/twilio_5_setwebhook.png)
    - The webhook should end in /sms. If you're using Glitch, then it should be something like `https://magnificent-class.glitch.com/sms`.
  
Now - everything should work! Try texting your number. You should see a response!

Your messages are probably prepented with the note `Sent from your Twilio trial account -`.
If you sign up with a form of payment at the [billing page](https://www.twilio.com/console/billing), you won't see the message anymore.

## Editing the conversation

All of the code that runs the conversation is in the file `conversation.py`.

This is the exact same code as what runs in the Jupyter Notebook! You can change the rules & patterns in this code to change how the Python server returns a message to Twilio (or, in other words, what text messages you receive as a response).

![imgs/glitch_3_conversation](imgs/glitch_3_conversation.png)

## Troubleshooting

If you don't receive any responses, you can check the logs in Glitch.
 ![imgs/glitch_logs](https://github.com/dantaeyoung/Ethicsware/blob/master/imgs/glitch_logs.png)

## Your server

You can also run this on your server! We're only using Glitch because it provides a handy way to create a server exposed to the internet.
