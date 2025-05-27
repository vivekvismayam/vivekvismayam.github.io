# Experienced Page Time in Salesforce

&nbsp;  

# You might have seen this green box with some values displaying at the top of your sandbox org, but are you really aware what is it(EPT) and what is it used for? 🧐 

**Experienced Page Time (EPT)** is how Salesforce measures the time it takes to download and display the entire content of a webpage in a browser window. 🚀 🚀 🚀 

Ever wondered how long it takes for a Lightning Experience page to fully load and display? Salesforce's Experienced Page Time (EPT) helps measure exactly that! 🌟

EPT is measured as the time from the page start to when no more activity occurs for at least two frames (~33 ms). The two extra frames help to avoid false positives due to asynchronous calls. These calls include any XMLHttpRequests (XHRs) activity, any storage activity, or any user interaction or client-side work of any kind in the main JavaScript thread. Read [here](https://help.salesforce.com/s/articleView?id=000392614&type=1)

📊 Why is EPT important?
It gives insights into page load times, helping admins and developers enhance the user experience in Salesforce.

## Ways to enable EPT monitoring in Lightning Experience

🔍 Here are two simple ways to enable EPT monitoring in Lightning Experience:

### 1️⃣ 𝐄𝐧𝐚𝐛𝐥𝐞 𝐋𝐢𝐠𝐡𝐭𝐧𝐢𝐧𝐠 𝐂𝐨𝐦𝐩𝐨𝐧𝐞𝐧𝐭 𝐃𝐞𝐛𝐮𝐠 𝐌𝐨𝐝𝐞
- Go to Setup and enable Lightning Component Debug Mode.
- Adds a counter to the header showing page load time and network bandwidth.

![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p10_1.jpg)

>⚠️ Note: This can slightly impact performance as component code isn't minified and caching is disabled.

***

### 2️⃣ 𝐌𝐨𝐝𝐢𝐟𝐲 𝐭𝐡𝐞 𝐔𝐑𝐋
- Add ```?𝘦𝘱𝘵𝘝𝘪𝘴𝘪𝘣𝘭𝘦=1``` to the end of your Lightning Experience URL.
- This shows the page load time counter in the header (but not network bandwidth).


![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p10_2.jpg)

>💡 Unlike enabling Lightning Component Debug Mode, the component code is minified and there will be less impact on performance time.

***

## Few Things to remember
- ⚠️ Avoid opening pages in a new tab or manually reloading them, as this includes the Lightning Framework bootstrap in the measurement, leading to skewed results.
- 💡 These simple tweaks can give you actionable insights to optimize performance in your Salesforce org.

>💡 Aim for a low EPT! It’s a sign of optimized performance and a well-tuned Salesforce environment. 

>SF documentation on [Experienced Page Time](https://help.salesforce.com/s/articleView?id=sf.technical_requirements_ept.htm&language=en_US&type=5) 


*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_salesforce-lightningexperience-performancemonitoring-activity-7271152071960084481-9VYs?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
