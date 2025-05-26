# Push Notifications on salesforce screen

&nbsp;  

# Have you ever thought on  how we can show Push Notifications on salesforce screen?🤔🤔🤔

It is a great way to alert your salesforce users about anything which needs immediate attention.
And It may not be as complex as you think!🪄🔔📲

&nbsp; 

Lets break this up in to 2 steps:🪛


## Create a Custom Notification Type
 
 
 👉Go to Setup > Notification Builder > Custom Notifications .   
 Create a new Custom Notification Type by giving name and supported channels(Desktop/Mobile)
 
 ![Image 1](/images/p5_2.jpg)


 ![Image 2](/images/p5_3.jpg)
 ***

## Trigger the notification
👉you can trigger notifications from APEX or Flows
    
### 🟢From Flow 
You can use Action element->select Action **'Send Custom Notification'** and pass in the needed details like :

        - 𝘊𝘶𝘴𝘵𝘰𝘮 𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯 𝘛𝘺𝘱𝘦 𝘐𝘥 - Record Id of Custom Notification Type
        - 𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯 𝘛𝘪𝘵𝘭𝘦 - Title for your notification
        - 𝘊𝘶𝘴𝘵𝘰𝘮 𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯 𝘔𝘦𝘴𝘴𝘢𝘨𝘦 - Message you want to show in Notification
        - 𝘙𝘦𝘤𝘪𝘱𝘪𝘦𝘯𝘵 𝘐𝘋𝘴 - A variable of type text with multiple values allowed
        - 𝘛𝘢𝘳𝘨𝘦𝘵 𝘐𝘋 - The record you need to open on clicking the push notification  
    etc

Here are few screenshots to understand this better:

![Image 4](/images/p5_4.jpg)
***

![Image 5](/images/p5_5.jpg)
***

![Image 6](/images/p5_6.jpg)
***

![Image 7](/images/p5_7.jpg)

***

### 🟢From Apex

You can use CustomNotification class to create a push notification as below. 

```Apex
    𝘔𝘦𝘴𝘴𝘢𝘨𝘪𝘯𝘨.𝘊𝘶𝘴𝘵𝘰𝘮𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯 𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯 = 𝘯𝘦𝘸 𝘔𝘦𝘴𝘴𝘢𝘨𝘪𝘯𝘨.𝘊𝘶𝘴𝘵𝘰𝘮𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯();
    𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘦𝘵𝘛𝘪𝘵𝘭𝘦('𝘈𝘱𝘦𝘹 𝘊𝘶𝘴𝘵𝘰𝘮 𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯');
    𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘦𝘵𝘉𝘰𝘥𝘺('𝘛𝘩𝘦 𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯𝘴 𝘢𝘳𝘦 𝘤𝘰𝘮𝘪𝘯𝘨 𝘧𝘳𝘰𝘮 𝘐𝘕𝘚𝘐𝘋𝘌 𝘵𝘩𝘦 𝘈𝘱𝘦𝘹!');
    𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘦𝘵𝘕𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯𝘛𝘺𝘱𝘦𝘐𝘥(𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯𝘛𝘺𝘱𝘦.𝘐𝘥);
    𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘦𝘵𝘛𝘢𝘳𝘨𝘦𝘵𝘐𝘥(𝘵𝘢𝘳𝘨𝘦𝘵𝘐𝘥);
    𝘯𝘰𝘵𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘦𝘯𝘥(𝘳𝘦𝘤𝘪𝘱𝘪𝘦𝘯𝘵𝘴𝘐𝘥𝘴); 
```

>please note this is rough code for understanding ,see the below Screenshot for exact code:
> ![Image 8](/images/p5_8.jpg)
>
>>🔗 🔗Here is the link to SF documentation on [CustomNotification Class](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_class_Messaging_CustomNotification.htm) 

>🔗 Here is a nice article on the same from [SF Ben](https://www.salesforceben.com/set-up-salesforce-push-notifications/) 

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_pushnotification-salesforce-sf-activity-7262473176356397058-a7Aq?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
