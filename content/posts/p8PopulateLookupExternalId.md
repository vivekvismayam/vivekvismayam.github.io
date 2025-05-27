+++
date = '2024-05-28T16:10:13+05:30'
title = 'Populate Lookups Using External Id from APIs'
slug='populate-lookup-external-id'
authors = ['Vivek']
tags = ['SalesforceRestExplorer','Admin','data','RestAPI']
categories= ['IT','Salesforce']
weight = 5
featuredImage ='https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p8_header.png'
featuredImagePreview ='https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p8_header.png'
summary="An external field on parent object can be used to populate the relation when creating/updating a child object record."
description="Populate Lookups Using External Id "
seriesNavigation=false
toc=false
+++
&nbsp;  

We all might have used External id field, which is useful when we need to identify records uniquely based on an external system identifiers. We can use these fields while creating or updating records to avoid creating any duplicates in normal scenarios.

## Did you know that you can use the same external id field to populate lookups❗ 

That is, an external field on parent object can be used to populate the relation when creating/updating a child object record from API.

Lets break this down by an example:

- 👉Lets assume i have 2 objects ```𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤``` and ```𝘊𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘤``` related by a lookup relationship.
- 👉```𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤``` has an external Id field ```"𝘚𝘶𝘣𝘚𝘺𝘴𝘵𝘦𝘮𝘐𝘥__𝘤"``` which hold Id from an external system.
- 👉I have a ```𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘤``` record with Name="𝘗𝘢𝘳𝘦𝘯𝘵001" and 𝘚𝘶𝘣𝘚𝘺𝘴𝘵𝘦𝘮𝘐𝘥__𝘤="𝘌𝘟𝘛𝘚𝘚1"

My objective is to create a new record of ```𝘊𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘤``` with parent as record "𝘗𝘢𝘳𝘦𝘯𝘵001". 


Normally we would use Id of parent record to populate this relationship.But mostly this salesforce id may not be available for External system. That is when we can use **𝘚𝘶𝘣𝘚𝘺𝘴𝘵𝘦𝘮𝘐𝘥** ,External Id field from parent to populate the "𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘳" relationship on child!✅

👉This can be used for update using patch method as well

>Endpoint : /𝘴𝘦𝘳𝘷𝘪𝘤𝘦𝘴/𝘥𝘢𝘵𝘢/𝘷60.0/𝘴𝘰𝘣𝘫𝘦𝘤𝘵𝘴/𝘊𝘩𝘪𝘭𝘥𝘖𝘣𝘫𝘦𝘤𝘵__𝘤  
>Method: 𝘗𝘰𝘴𝘵  
>Body:
>```Json
>    {
>       "𝘕𝘢𝘮𝘦":"𝘊𝘩𝘪𝘭𝘥𝘙𝘦𝘤𝘰𝘳𝘥001",
>       "𝘗𝘢𝘳𝘦𝘯𝘵𝘖𝘣𝘫𝘦𝘤𝘵__𝘳":
>       {
>           "𝘚𝘶𝘣𝘚𝘺𝘴𝘵𝘦𝘮𝘐𝘥__𝘤":"𝘌𝘟𝘛𝘚𝘚1"
>       }
>    }
>```


Below is a demo of the same with the help of Salesforce Rest Explorer VS Code Extension!🎩🪄
<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7265221343506235392?compact=1" height="399" width="100%" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>


>watch demo video on [linkedin](https://www.linkedin.com/posts/vivekvismayam_we-all-might-have-used-external-id-field-activity-7265221465342386176-cIZ3?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)

>SF documentation on [Relating Records by Using an External ID](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/langCon_apex_dml_nested_object.htm) in **Apex**


*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_we-all-might-have-used-external-id-field-activity-7265221465342386176-cIZ3?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***