# Transfer Records Using SF CLI Command❗

&nbsp;  

## What Is the easiest way to transfer few records and child records between two sandboxes/orgs❓


Definitely it is using SF CLI command ```'𝘴𝘧 𝘥𝘢𝘵𝘢 𝘦𝘹𝘱𝘰𝘳𝘵 𝘵𝘳𝘦𝘦'``` and ```'𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘵𝘳𝘦𝘦'```!🪄

&nbsp; 

Well, How Exactly❓❓❓  


Lets say, we want to move few records of **ParentObject__c** and all related child records **ChildObject__c** from one sandbox to other.📲

&nbsp; 


Lets break this down to 2 steps!


1️⃣ 𝐄𝐱𝐩𝐨𝐫𝐭𝐢𝐧𝐠 𝐃𝐚𝐭𝐚 𝐟𝐫𝐨𝐦 𝐬𝐨𝐮𝐫𝐜𝐞 𝐨𝐫𝐠 𝐚𝐬 𝐉𝐒𝐎𝐍 𝐅𝐢𝐥𝐞𝐬: Open the terminal run the ```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘦𝘹𝘱𝘰𝘳𝘵 𝘵𝘳𝘦𝘦``` command as below:

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘦𝘹𝘱𝘰𝘳𝘵 𝘵𝘳𝘦𝘦 --𝘲𝘶𝘦𝘳𝘺 "𝘚𝘦𝘭𝘦𝘤𝘵 𝘐𝘥,𝘕𝘢𝘮𝘦,(𝘚𝘦𝘭𝘦𝘤𝘵 𝘐𝘥,𝘕𝘢𝘮𝘦 𝘧𝘳𝘰𝘮 C𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘳) 𝘧𝘳𝘰𝘮 𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤" --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 <𝘴𝘰𝘶𝘳𝘤𝘦 𝘖𝘳𝘨>```

A JSON File will be created in the root directory with the name "𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤-𝘊𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘤.𝘫𝘴𝘰𝘯"

2️⃣ 𝐈𝐦𝐩𝐨𝐫𝐭 𝐉𝐒𝐎𝐍 𝐃𝐚𝐭𝐚 𝐭𝐨 𝐓𝐚𝐫𝐠𝐞𝐭 𝐎𝐫𝐠: Now you can import it to your new org using the command 

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘵𝘳𝘦𝘦 --𝘧𝘪𝘭𝘦𝘴 𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤-𝘊𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘤.𝘫𝘴𝘰𝘯 --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 <𝘵𝘢𝘳𝘨𝘦𝘵 𝘖𝘳𝘨>```

You can import multiple files by giving filenames comma separated in ```--files``` flag.For Eg  
```--files file1.json,file2.json``` 

&nbsp; 


Tada! Done!🪄🪄🪄

&nbsp; 

Here is a quick demo on the same

<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7260626861016178688?compact=1" height="399" width="100%" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>

>watch demo video on [linkedin](https://www.linkedin.com/posts/vivekvismayam_what-is-the-easiest-way-to-transfer-few-records-activity-7260626983942774785-MxmU?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)

>SF documentation on [data export tree](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_data_commands_unified.htm#cli_reference_data_export_tree_unified) says, The SOQL query can return a maximum of 2,000 records. But I was able to retrieve 10000 records from an org and was able to get even more records(20000) by setting *"maxQueryLimit"* in sfdx config file. Still i think it would be safe if we stick to 2000 count

🟥 Remember! 
1. You should have sf cli installed!
2. The objects and fields is expected in target org as source org 
3. Include all required fields in the query while running export command or you will get Required field missing error while importing data in target org

There is a very interesting flag ```--plan``` which we will discuss in another post❗


>Do Check Salesforce Documentation on [data export tree](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_data_commands_unified.htm#cli_reference_data_export_tree_unified) and [data import tree](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_data_commands_unified.htm#cli_reference_data_import_tree_unified)

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_what-is-the-easiest-way-to-transfer-few-records-activity-7260626983942774785-MxmU?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
