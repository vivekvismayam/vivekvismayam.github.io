# 18 Digit ID In Apex 


&nbsp; 

**Here is something interesting in Apex which you need to be aware of!📢**


See the below code 🕵️‍♀️🕵️‍♀️🕵️‍♀️



```apex
𝘓𝘪𝘴𝘵<𝘐𝘥> 𝘪𝘥𝘓𝘪𝘴𝘵 = 𝘯𝘦𝘸 𝘓𝘪𝘴𝘵<𝘐𝘥>{'𝟎𝟎𝟏𝐆𝐁𝟎𝟎𝟎𝟎𝟑𝐄𝐎𝐌𝐈𝟖','𝟎𝟎𝟏𝐆𝐁𝟎𝟎𝟎𝟎𝟑𝐄𝐎𝐅𝐜𝐣'};//15 𝘥𝘪𝘨𝘪𝘵 𝘪𝘥𝘴
 𝘧𝘰𝘳(𝘐𝘥 𝘪𝘥𝘪𝘵𝘦𝘮:𝘪𝘥𝘓𝘪𝘴𝘵){
 𝘚𝘺𝘴𝘵𝘦𝘮.𝘥𝘦𝘣𝘶𝘨(𝘪𝘥𝘪𝘵𝘦𝘮);
 }
```
## ⚠Note: Do not ever hardcode Id🚫. This code is just for demonstration purpose📺📺📺


What do you think the debug will look like🔎? Will the ids in debug log look same as we entered🔎?

&nbsp; 

- 👉Nope you will find the ids are logged as 18 digit ids!
- 👉Did you know that in Apex, when you work with Salesforce IDs (like adding them to a 𝘓𝘪𝘴𝘵<𝘐𝘥>), Salesforce automatically converts 15-character IDs to 18-character Ids and that is why this is happening.
- 👉Still you can use 𝘓𝘪𝘴𝘵<𝘚𝘵𝘳𝘪𝘯𝘨> if you dont want this to happen.

See below to view the output

![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p14_1.jpg)


*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_apex-salesforce-activity-7275868887659782144-v7pu?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
