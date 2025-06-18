# Why a User Couldn’t Change Opportunity Currency — Even with Full Access💡

&nbsp;  
## A puzzling issue in our Salesforce org


Recently encountered a puzzling issue in our Salesforce org — a user with Create, Read, and Edit access on the Opportunity object, including Field-Level Security (FLS) for the CurrencyIsoCode field and full record ownership, was unable to update the Opportunity Currency from EUR (Euro) to DKK (Danish Krone).  
User was able to update other fields, so this was clearly not a record access issue.  

The error message?

>❗ "Oops... you don't have the necessary privileges to edit this record."

This looks like a standard field access issue, but user had access to all needed fields as we were expecting.

&nbsp; 

We ruled out:
- FLS for the field is provided to User's Profile ✅
- No Oppty Line Items, Quotes, or Orders related ✅
- Confirmed record ownership✅
- No validation rules, flows, or triggers blocking it✅
- Issue didn’t occur for System Admins✅

***


<div style="text-align: center;">

#![Gif 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p17_1.gif)

</div>

It was quite frustrating at first, but I was genuinely glad to discover that it led me to something I hadn’t come across before — a chance to learn and understand a lesser-known behavior in Salesforce

&nbsp; 

### 🧩 Root Cause 

The user didn’t have read access to a custom field ```Revenue__c```, which was being used in *Opportunity Splits*.
Even though the field wasn't being directly edited, Salesforce still required visibility to it — a dependency not clearly reflected in the error message. Once read access to ```Revenue__c``` was granted, the currency update worked immediately.

To find oppty split field, Go to Setup ->Opportunities -> Opportunity Splits > Settings, for the column 'Split Field'. it will show you the object and the field name of the split type field.
Below is a snap on how to find the Opportunity split field in your org!
![Image 3](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p17_3.jpeg)

&nbsp;

💬 I found similar experiences discussed in the Trailblazer Community, and Salesforce support mentioned that they’ll consider creating a knowledge article to document this s — until then, this might help others scratching their heads on similar issues!

>Here is a Trailblazer Community Discussion On the same : https://trailhead.salesforce.com/trailblazer-community/feed/0D54S00000A8AkISAV

### 📌 Takeaway:
> Sometimes field dependencies go deeper than the surface. 

If users can’t update the Opportunity currency despite having all required access — check for hidden dependencies like Opportunity Split fields. These can silently block operations without any clear indication.  
Big thanks to Salesforce Support for the help in getting this sorted!

<div style="text-align: center;">

#![Gif 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p17_2.gif)

</div>

> Always approach issues systematically — **debug with reason, try out possibilities, and think critically.** But if nothing works after a fair attempt, don’t hesitate to reach out to Salesforce Support. It saves time and often reveals insights you might not uncover alone.



***
