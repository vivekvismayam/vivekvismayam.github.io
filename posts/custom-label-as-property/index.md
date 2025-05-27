# Custom Label As A Property In Lightning Page & LWR Site🔖🔖🔖

&nbsp;  
 
## Did you know that we can use Custom labels as Property input values in Lightning App Builder 

Using this format

> ```{!$𝘓𝘢𝘣𝘦𝘭.𝘊𝘶𝘴𝘵𝘰𝘮𝘓𝘢𝘣𝘦𝘭𝘕𝘢𝘮𝘦}. ```


Probably Yes, as we all have seen the help text on property editor in builder! 🔖
 
But lets say what if we want to the same in an LWR Site💡. **We can make it work by adding the default namespace(‘c’) to it and note, you dont need $** - 
> ```{!𝘓𝘢𝘣𝘦𝘭.𝘯𝘢𝘮𝘦𝘴𝘱𝘢𝘤𝘦.𝘊𝘶𝘴𝘵𝘰𝘮𝘓𝘢𝘣𝘦𝘭𝘕𝘢𝘮𝘦}```

For Eg:
>```{!𝘓𝘢𝘣𝘦𝘭.c.MyLabel}```
>
>*Where 𝐌𝐲𝐋𝐚𝐛𝐞𝐥 is my custom label Name*


 Here is the custom label i have created in my developer edition org👨‍💻


![Image 3](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p1_3.jpg)


***

This is how we can reference the Custom Label ```{!𝘓𝘢𝘣𝘦𝘭.c.MyLabel}``` in Lightning App Builder


![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p1_1.jpg)


***


This is how we can reference the Custom Label ```{!𝘓𝘢𝘣𝘦𝘭.c.MyLabel}``` in LWR Site!


![Image 2](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p1_2.jpg)

***
 
⚠ As mentioned above I have tried this in LWR site and its working perfectly, but not working in aura sites for reasons I am unaware of❗🤷‍♂️

>Bonus Tip 🎯: You can set the default attribute of property in XML file as 
>
>  ```{!$𝘓𝘢𝘣𝘦𝘭.𝘊𝘶𝘴𝘵𝘰𝘮𝘓𝘢𝘣𝘦𝘭𝘕𝘢𝘮𝘦}```
>
>For Eg:
>
>```<𝘱𝘳𝘰𝘱𝘦𝘳𝘵𝘺 𝘵𝘺𝘱𝘦="𝘚𝘵𝘳𝘪𝘯𝘨" 𝘯𝘢𝘮𝘦="𝘪𝘯𝘱𝘶𝘵" 𝘭𝘢𝘣𝘦𝘭="𝘐𝘯𝘱𝘶𝘵𝘛𝘦𝘹𝘵" 𝘥𝘦𝘧𝘢𝘶𝘭𝘵={!$𝘓𝘢𝘣𝘦𝘭.𝘔𝘺𝘓𝘢𝘣𝘦𝘭}" />```
>
>Where 𝐌𝐲𝐋𝐚𝐛𝐞𝐥 is my Custom Label Name 
>
>This way the value stored in Custom label is taken as default value and you don’t have to change this in code each and every time!🚀

***


You can find the code for LWC components used in [my github repo](https://github.com/vivekvismayam/Demo)
- LWC Component Name : *labelInputComponent*

***

*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_lwc-property-builder-activity-7259568748183879680-WEhL?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
