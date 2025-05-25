# Import Files Using Bulk API from Salesforce CLI 

&nbsp;  

## You can now use the power of *Bulk API* to 𝐢𝐦𝐩𝐨𝐫𝐭 𝐚 𝐥𝐚𝐫𝐠𝐞 𝐧𝐮𝐦𝐛𝐞𝐫 𝐨𝐟 𝐫𝐞𝐜𝐨𝐫𝐝𝐬 𝐢𝐧𝐭𝐨 𝐚 𝐒𝐚𝐥𝐞𝐬𝐟𝐨𝐫𝐜𝐞 𝐨𝐛𝐣𝐞𝐜𝐭 𝐟𝐫𝐨𝐦 𝐚 𝐜𝐨𝐦𝐦𝐚-𝐬𝐞𝐩𝐚𝐫𝐚𝐭𝐞𝐝 𝐯𝐚𝐥𝐮𝐞𝐬 (𝐂𝐒𝐕) 𝐟𝐢𝐥𝐞  with the new data import bulk command 💪.

📢📢📢

Update sf cli to the latest version to use this(*## 2.64.6 (October 30, 2024) [stable]*).All the records on the csv file should be same **Salesforce object**


Use the ```--𝘴𝘰𝘣𝘫𝘦𝘤𝘵``` flag to specify the Salesforce object.

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘣𝘶𝘭𝘬 --𝘧𝘪𝘭𝘦 <𝘧𝘪𝘭𝘦 𝘯𝘢𝘮𝘦> --𝘴𝘰𝘣𝘫𝘦𝘤𝘵 <𝘴𝘶𝘣𝘫𝘦𝘤𝘵 𝘈𝘗𝘐 𝘕𝘢𝘮𝘦> --𝘸𝘢𝘪𝘵 <𝘸𝘢𝘪𝘵 𝘵𝘪𝘮𝘦 𝘪𝘯 𝘮𝘪𝘯𝘶𝘵𝘦𝘴> --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 <𝘰𝘳𝘨 𝘢𝘭𝘪𝘢𝘴>```

&nbsp;  

👉For example, 

Below command imports Account records from the **accounts.csv88 file into an org with alias "my-scratch":

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘣𝘶𝘭𝘬 --𝘧𝘪𝘭𝘦 𝘢𝘤𝘤𝘰𝘶𝘯𝘵𝘴.𝘤𝘴𝘷 --𝘴𝘰𝘣𝘫𝘦𝘤𝘵 𝘈𝘤𝘤𝘰𝘶𝘯𝘵 --𝘸𝘢𝘪𝘵 10 --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 𝘮𝘺-𝘴𝘤𝘳𝘢𝘵𝘤𝘩```

Thats All🪄🪄🪄

SF CLI Takes care of the rest!🧙✨

👉As Bulk imports takes time depending on how many records are in the CSV file the command time out after the specified wait time (10 minutes above).in this case it displays a job ID that you can pass to the new data import resume command to see the status and results of the original export.

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘳𝘦𝘴𝘶𝘮𝘦 --𝘫𝘰𝘣-𝘪𝘥 <𝘑𝘰𝘣 𝘐𝘥>```


Resume the most recently run bulk import job for an org with alias my-scratch:

>```𝘴𝘧 𝘥𝘢𝘵𝘢 𝘪𝘮𝘱𝘰𝘳𝘵 𝘳𝘦𝘴𝘶𝘮𝘦 --𝘶𝘴𝘦-𝘮𝘰𝘴𝘵-𝘳𝘦𝘤𝘦𝘯𝘵 --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 𝘮𝘺-𝘴𝘤𝘳𝘢𝘵𝘤𝘩```

📝Here is a quick demo on the same, the data is queried before and after running the command to verify the records are inserted.
<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7259929552246722561?compact=1" height="399" width="100%" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>


>watch demo video on [linkedin](https://www.linkedin.com/posts/vivekvismayam_%F0%9D%90%8D%F0%9D%90%9E%F0%9D%90%B0-%F0%9D%90%82%F0%9D%90%A8%F0%9D%90%A6%F0%9D%90%A6%F0%9D%90%9A%F0%9D%90%A7%F0%9D%90%9D-%F0%9D%90%A2%F0%9D%90%A7-%F0%9D%90%AC%F0%9D%90%9F-%F0%9D%90%9C%F0%9D%90%A5%F0%9D%90%A2-activity-7259929705787609088-c2Kt?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)

>SF documentation on [data import bulk](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_data_commands_unified.htm#cli_reference_data_import_bulk_unified) 
>SF documentation on [Prepare Data to Ingest](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_data_commands_unified.htm#cli_reference_data_import_bulk_unified). That is creating csv file for data import.

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_%F0%9D%90%8D%F0%9D%90%9E%F0%9D%90%B0-%F0%9D%90%82%F0%9D%90%A8%F0%9D%90%A6%F0%9D%90%A6%F0%9D%90%9A%F0%9D%90%A7%F0%9D%90%9D-%F0%9D%90%A2%F0%9D%90%A7-%F0%9D%90%AC%F0%9D%90%9F-%F0%9D%90%9C%F0%9D%90%A5%F0%9D%90%A2-activity-7259929705787609088-c2Kt?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
