+++
date = '2024-05-28T16:10:13+05:30'
title = 'Pass sObject to an Apex Method From LWC Component📲'
slug='pass-sobject-lwc-to-apex'
authors = ['Vivek']
tags = ['LWC','Apex','data',]
categories= ['IT','Salesforce']
weight = 5
featuredImage ='https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p9_header.png'
featuredImagePreview ='https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p9_header.png'
summary="How to pass an sobject record to an apex method from LWC component"
description="Pass sObject to an apex method from LWC component"
seriesNavigation=false
toc=false
+++
&nbsp;  


One of the most interesting and useful thing i came across while working with LWC, is the ability to **pass an 𝘴𝘖𝘣𝘫𝘦𝘤𝘵 from LWC component to Apex**🧙. This actually saves us from writing wrapper classes and assigning the fields from the same in apex in case we need to update the same object.🪄

If you have not used it yet, here is an example🔬:

👉Lets say, you need to update some fields on an Account from a LWC component based on user action. 
Of course ```𝘶𝘱𝘥𝘢𝘵𝘦𝘙𝘦𝘤𝘰𝘳𝘥``` from ```'𝘭𝘪𝘨𝘩𝘵𝘯𝘪𝘯𝘨/𝘶𝘪𝘙𝘦𝘤𝘰𝘳𝘥𝘈𝘱𝘪'``` should be the first option we should be considering✅. But what if user normally should not have FLS to the field 🤔💭. Or the org is poorly setup and you dont have the time or authority to fix things. 

This is where we can utilize the approach which i was mentioning above.📈

👉You can create a js object with field to edit from LWC and pass it to an Apex method without using any wrapper.🚀
```JS
 𝘭𝘦𝘵 𝘳𝘦𝘤𝘰𝘳𝘥 = {
 𝘴𝘰𝘣𝘫𝘦𝘤𝘵𝘛𝘺𝘱𝘦: "𝘈𝘤𝘤𝘰𝘶𝘯𝘵",
 𝘐𝘥: 𝘵𝘩𝘪𝘴.𝘳𝘦𝘤𝘰𝘳𝘥𝘐𝘥,
 𝘍𝘪𝘦𝘭𝘥𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦__𝘤: "𝘕𝘦𝘸 𝘝𝘢𝘭𝘶𝘦"
 };
```
👉And then you can pass the object to an apex method from LWC component 🚀

```JS
 𝘶𝘱𝘥𝘢𝘵𝘦𝘈𝘤𝘤𝘰𝘶𝘯𝘵𝘍𝘪𝘦𝘭𝘥𝘴({𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦:𝘳𝘦𝘤𝘰𝘳𝘥})
 .𝘵𝘩𝘦𝘯((𝘳𝘦𝘴) => 𝘤𝘰𝘯𝘴𝘰𝘭𝘦.𝘭𝘰𝘨("𝘳𝘦𝘤𝘰𝘳𝘥 𝘶𝘱𝘥𝘢𝘵𝘦𝘥"))
 .𝘤𝘢𝘵𝘤𝘩((𝘦𝘳𝘳𝘰𝘳) => 𝘤𝘰𝘯𝘴𝘰𝘭𝘦.𝘦𝘳𝘳𝘰𝘳("𝘦𝘳𝘳𝘰𝘳: " + 𝘑𝘚𝘖𝘕.𝘴𝘵𝘳𝘪𝘯𝘨𝘪𝘧𝘺(𝘦𝘳𝘳𝘰𝘳)));
```


👉Now the Apex method can written as below🚀:

```apex
𝘱𝘶𝘣𝘭𝘪𝘤 𝘸𝘪𝘵𝘩 𝘴𝘩𝘢𝘳𝘪𝘯𝘨 𝘤𝘭𝘢𝘴𝘴 𝘙𝘦𝘤𝘪𝘦𝘷𝘦𝘴𝘖𝘣𝘫𝘦𝘤𝘵𝘍𝘳𝘰𝘮𝘓𝘞𝘊 {
 @𝘈𝘶𝘳𝘢𝘌𝘯𝘢𝘣𝘭𝘦𝘥(𝘤𝘢𝘤𝘩𝘦𝘢𝘣𝘭𝘦=𝘧𝘢𝘭𝘴𝘦)
 𝘱𝘶𝘣𝘭𝘪𝘤 𝘴𝘵𝘢𝘵𝘪𝘤 𝘉𝘰𝘰𝘭𝘦𝘢𝘯 𝘶𝘱𝘥𝘢𝘵𝘦𝘈𝘤𝘤𝘰𝘶𝘯𝘵𝘍𝘪𝘦𝘭𝘥𝘴(𝘈𝘤𝘤𝘰𝘶𝘯𝘵 𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦){
 𝘈𝘤𝘤𝘰𝘶𝘯𝘵 𝘢𝘤𝘤=𝘯𝘦𝘸 𝘈𝘤𝘤𝘰𝘶𝘯𝘵(𝘐𝘥=𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦.𝘐𝘥);
 𝘪𝘧(𝘚𝘵𝘳𝘪𝘯𝘨.𝘐𝘴𝘕𝘰𝘵𝘉𝘭𝘢𝘯𝘬(𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦?.𝘍𝘪𝘦𝘭𝘥𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦__𝘤))
 {
 𝘢𝘤𝘤.𝘍𝘪𝘦𝘭𝘥𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦__𝘤=𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦.𝘍𝘪𝘦𝘭𝘥𝘛𝘰𝘜𝘱𝘥𝘢𝘵𝘦__𝘤;
 }
 𝘶𝘱𝘥𝘢𝘵𝘦 𝘢𝘤𝘤;
 𝘳𝘦𝘵𝘶𝘳𝘯 𝘵𝘳𝘶𝘦; 
 }
}

```

>Note that i have created new Account variable acc, reassigned the field we are expecting to this new variable from accountToUpdate variable and updated acc instead of directly updating accountToUpdate🚫. This is because the object accountToUpdate is created from front end JS and can be manipulated to update unintended fields by adding extra fields from front end. So as a better security practice👮, i believe its better to add this check from Apex side🕵️‍♀️.
You can pass a list of records in similar way!🔮




You can find the code for LWC components used in [my github repo](https://github.com/vivekvismayam/Demo)
- LWC Component Name : *passSobjectToApex*
- Apex Class Name: *RecievesObjectFromLWC.cls*

***

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_one-of-the-most-interesting-and-useful-thing-activity-7267897877102772224-eqg9?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***