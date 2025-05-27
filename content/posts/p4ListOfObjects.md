+++
date = '2024-06-03T16:10:13+05:30'
title = 'Get Complete List Of Objects Using SF CLI Command📝📝📝'
slug='list-of-objects-cli'
authors = ['Vivek']
tags = ['data','CLI','Admin']
categories= ['IT','Salesforce']
weight = 0
featuredImage ='/images/generic_header.png'
featuredImagePreview ='/images/generic_header.png'
summary="Easiest way to get list of objects if you can execute SF CLI"
description="Easiest way to get list of objects if you can execute SF CLI"
seriesNavigation=false
toc=false
+++
&nbsp;  

## Suppose you need to get the list of all objects on your org or a list of Custom objects or Standard objects separately📕📗📃. 
## What is the approach you will go for❓


wait a minute to think!

🕓🕕🕚

&nbsp; 


The easiest way would be using *```'𝘴𝘧 𝘴𝘰𝘣𝘫𝘦𝘤𝘵 𝘭𝘪𝘴𝘵'```* command in **SF CLI!**🗿🚀


- 👉use flag ```'--𝘴𝘰𝘣𝘫𝘦𝘤𝘵'``` to get all|custom|standard objects
Eg: 

>```𝘴𝘧 𝘴𝘰𝘣𝘫𝘦𝘤𝘵 𝘭𝘪𝘴𝘵 --𝘴𝘶𝘣𝘫𝘦𝘤𝘵 𝘤𝘶𝘴𝘵𝘰𝘮```

- 👉use ```'-𝘰'``` or ```'--𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨'``` optionally. This will be needed if you run the command out of sfdx project structure or no default org is selected or you want list from a non defaulted org

- 👉going a step forward, if you need to get this in a csv file, add ```> <filename>.csv``` in the command🔮🪄

For Eg:
> ```𝘴𝘧 𝘴𝘰𝘣𝘫𝘦𝘤𝘵 𝘭𝘪𝘴𝘵 --𝘴𝘶𝘣𝘫𝘦𝘤𝘵 𝘤𝘶𝘴𝘵𝘰𝘮 > 𝘤𝘶𝘴𝘵𝘰𝘮𝘰𝘣𝘫𝘦𝘤𝘵𝘴.𝘤𝘴𝘷```

or

> ```𝘴𝘧 𝘴𝘰𝘣𝘫𝘦𝘤𝘵 𝘭𝘪𝘴𝘵 --𝘴𝘶𝘣𝘫𝘦𝘤𝘵 𝘴𝘵𝘢𝘯𝘥𝘢𝘳𝘥 > 𝘴𝘵𝘢𝘯𝘥𝘢𝘳𝘥𝘰𝘣𝘫𝘦𝘤𝘵𝘴.𝘤𝘴𝘷```

## Note!
## 👉You will get only sobject API Names using this method.

Here is a quick demo on the same

<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7261724894722236416?compact=1" height="399" width="100%" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>

>watch demo video on [linkedin](https://www.linkedin.com/posts/vivekvismayam_sf-salesforce-cli-activity-7261725058748825600-L7Oi?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)

>Do Check Salesforce Documentation on [sobject list](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_sobject_commands_unified.htm#cli_reference_sobject_list_unified) 

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_sf-salesforce-cli-activity-7261725058748825600-L7Oi?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***