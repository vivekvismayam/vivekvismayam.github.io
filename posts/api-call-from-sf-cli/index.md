# Quick Tip! Make An Authenticated HTTP Request using Salesforce CLI 🚀 


&nbsp; 

## 🚀Quick Tip! Make An Authenticated HTTP Request using Salesforce CLI 🚀 

🟢You can use ```'𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵'``` command to make an api callout to your salesforce org using salesforce cli.
![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p13_1.jpg)
&nbsp; 
![Image 2](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p13_2.jpg)
***

🟢For quick start here are some examples:

 - 👉List information about limits in the org with alias "my-org":
 >```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 '𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/𝘭𝘪𝘮𝘪𝘵𝘴' --𝘵𝘢𝘳𝘨𝘦𝘵-𝘰𝘳𝘨 𝘮𝘺-𝘰𝘳𝘨```
 - 👉List all endpoints in your default org; write the output to a file called "output.txt" and include the HTTP response status and headers: 
 >```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 '/𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/' --𝘴𝘵𝘳𝘦𝘢𝘮-𝘵𝘰-𝘧𝘪𝘭𝘦 𝘰𝘶𝘵𝘱𝘶𝘵.𝘵𝘹𝘵 --𝘪𝘯𝘤𝘭𝘶𝘥𝘦```
 - 👉Get the response in XML format by specifying the "Accept" HTTP header:
 > ```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 '/𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/𝘭𝘪𝘮𝘪𝘵𝘴' --𝘩𝘦𝘢𝘥𝘦𝘳 '𝘈𝘤𝘤𝘦𝘱𝘵: 𝘢𝘱𝘱𝘭𝘪𝘤𝘢𝘵𝘪𝘰𝘯/𝘹𝘮𝘭'```

 - 👉Create an account record using the POST method; specify the request details directly in the "--body" flag:
 >  ```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 /𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/𝘴𝘰𝘣𝘫𝘦𝘤𝘵𝘴/𝘢𝘤𝘤𝘰𝘶𝘯𝘵 --𝘣𝘰𝘥𝘺 "{\"𝘕𝘢𝘮𝘦\" : \"𝘈𝘤𝘤𝘰𝘶𝘯𝘵 𝘧𝘳𝘰𝘮 𝘙𝘌𝘚𝘛 𝘈𝘗𝘐\",\"𝘚𝘩𝘪𝘱𝘱𝘪𝘯𝘨𝘊𝘪𝘵𝘺\" : \"𝘉𝘰𝘪𝘴𝘦\"}" --𝘮𝘦𝘵𝘩𝘰𝘥 𝘗𝘖𝘚𝘛```

 - 👉Create an account record using the information in a file called "info.json" (note the @ prefixing the file name):
 >```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 '/𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/𝘴𝘰𝘣𝘫𝘦𝘤𝘵𝘴/𝘢𝘤𝘤𝘰𝘶𝘯𝘵' --𝘣𝘰𝘥𝘺 @𝘪𝘯𝘧𝘰.𝘫𝘴𝘰𝘯 --𝘮𝘦𝘵𝘩𝘰𝘥 𝘗𝘖𝘚𝘛```

 - 👉Update an account record using the PATCH method:
 >```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 '/𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷56.0/𝘴𝘰𝘣𝘫𝘦𝘤𝘵𝘴/𝘢𝘤𝘤𝘰𝘶𝘯𝘵/<𝘈𝘤𝘤𝘰𝘶𝘯𝘵 𝘐𝘋>' --𝘣𝘰𝘥𝘺 "{\"𝘉𝘪𝘭𝘭𝘪𝘯𝘨𝘊𝘪𝘵𝘺\": \"𝘚𝘢𝘯 𝘍𝘳𝘢𝘯𝘤𝘪𝘴𝘤𝘰\"}" --𝘮𝘦𝘵𝘩𝘰𝘥 𝘗𝘈𝘛𝘊𝘏```

🟢You can also store the values for the request header, body, and so on, in a file as below 
 ```Json
 {
 𝘶𝘳𝘭: { 𝘳𝘢𝘸: 𝘴𝘵𝘳𝘪𝘯𝘨 } | 𝘴𝘵𝘳𝘪𝘯𝘨;
 𝘮𝘦𝘵𝘩𝘰𝘥: '𝘎𝘌𝘛', '𝘗𝘖𝘚𝘛', '𝘗𝘜𝘛', '𝘗𝘈𝘛𝘊𝘏', '𝘏𝘌𝘈𝘋', '𝘋𝘌𝘓𝘌𝘛𝘌', '𝘖𝘗𝘛𝘐𝘖𝘕𝘚', '𝘛𝘙𝘈𝘊𝘌';
 𝘥𝘦𝘴𝘤𝘳𝘪𝘱𝘵𝘪𝘰𝘯?: 𝘴𝘵𝘳𝘪𝘯𝘨;
 𝘩𝘦𝘢𝘥𝘦𝘳: 𝘴𝘵𝘳𝘪𝘯𝘨 | 𝘈𝘳𝘳𝘢𝘺<𝘙𝘦𝘤𝘰𝘳𝘥<𝘴𝘵𝘳𝘪𝘯𝘨, 𝘴𝘵𝘳𝘪𝘯𝘨>>;
 𝘣𝘰𝘥𝘺: { 𝘮𝘰𝘥𝘦: '𝘳𝘢𝘸' | '𝘧𝘰𝘳𝘮𝘥𝘢𝘵𝘢'; 𝘳𝘢𝘸: 𝘴𝘵𝘳𝘪𝘯𝘨; 𝘧𝘰𝘳𝘮𝘥𝘢𝘵𝘢: 𝘍𝘰𝘳𝘮𝘋𝘢𝘵𝘢 };
 }
```
 and then you then specifythe same in a callout with the --𝘧𝘪𝘭𝘦 flag.
 >```𝘴𝘧 𝘢𝘱𝘪 𝘳𝘦𝘲𝘶𝘦𝘴𝘵 𝘳𝘦𝘴𝘵 --𝘧𝘪𝘭𝘦 𝘮𝘺𝘍𝘪𝘭𝘦.𝘫𝘴𝘰𝘯```


>Salesforce CLI uses this schema to mimic Postman schemas and both share similar properties. you can build an API call using Postman, export and save it to a file, and then use the file as a value to this flag.✅✅✅

## ⚠Please do note that this feature is still in beta, so use wisely!!

>🔗Do Check Salesforce Documentation on [api request rest (Beta)](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_api_commands_unified.htm#cli_reference_api_request_rest_unified) 

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_%F0%9D%90%90%F0%9D%90%AE%F0%9D%90%A2%F0%9D%90%9C%F0%9D%90%A4-%F0%9D%90%AD%F0%9D%90%A2%F0%9D%90%A9-%F0%9D%90%8C%F0%9D%90%9A%F0%9D%90%A4%F0%9D%90%9E-%F0%9D%90%80%F0%9D%90%A7-%F0%9D%90%80%F0%9D%90%AE%F0%9D%90%AD-activity-7273690257751953409-Pd6N?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
