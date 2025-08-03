# 3 Salesforce CLI - Apex Commands Every Apex Developer Should Know🧑‍💻


## 💻 3 Salesforce CLI Commands Every Apex Developer Should Be Using

If you work with Apex daily, you know how time-consuming it can be to open dev console, run tests, and pull logs manually.

Luckily, Salesforce CLI (now moving toward the sf namespace) makes life a lot easier. Here are 3 commands that have saved me hours —  and honestly, I wish I started using them sooner.

---

### Apex Get Log📃
>🔍 `sf apex get log` — No More Clicking Through Debug Logs

Ever had to:
* Run some Apex in the Dev Console
* Go to Setup → Debug Logs
* Download the log
* Open it in VS Code just to find out what went wrong?
This command saves you from all that:  
`sf apex get log`  
It pulls the **debug logs** for your user right into your system.  
#### 💡 Flags to keep in mind!!
* 🏀`--log-id`: Lets you fetch the log by Id.  
  **`sf apex get log --log-id <log id> `**
![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_1.png)
  >📌Bonus Tip: Use `sf apex list log` to get a list of logs with Ids and you can use this id in above command to fetch the log!
  >![Image 2](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_2.png)
* 🏀`--number`: Lets you fetch the **last N logs**.  
  **`sf apex get log --number 3`**
* 🏀`--output-dir`: directory for saving the log files (absolute path or relative to the current working directory).  
  **`sf apex get log --number 2 --output-dir ./`**
  ![Image 3](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_3.png)

Super helpful when you're debugging tests or checking what your code actually did behind the scenes, without opening the developer console!!
>📚Do read more about [apex get log](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_apex_commands_unified.htm#cli_reference_apex_get_log_unified) from Salesforce documentation

---
### Apex Run Test🧪
>✅ `sf apex run test` — Run Tests Fast, Get Results Instantly (Or Asynchronously)  

Why wait for tests to run in the UI when you can do it right from the terminal?  
**`sf apex run test --class-names MyTestClass`**  
This runs the test class and gives you a command with test run id to retrieve test results  
>Run with --synchronous or increase --wait timeout to wait for results.
![Image 4](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_4.png)


#### 💡 Flags to keep in mind!!

* 🏀`--synchronous`: Run it synchronously and wait for results (recommended for local dev).
    ![Image 5](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_5.png)
* 🏀`--wait`: specify a wait time in mins and wait for results.
    ![Image 6](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_6.png)
* 🏀`--concise`: Keep the output clean and to the point.
    ![Image 7](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_7.png)
* 🏀`--output-dir `: Execute test and save results to a local directory `--output-dir <path to outputdir>`
* 🏀`--result-format`: Choose how the results show up – `human` (easy to read), `json` (for automation), or `tap`.

Perfect for quickly checking if your fix worked — or catching that one line of code that broke everything.
>📚Do read more about [apex run test](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_apex_commands_unified.htm#cli_reference_apex_run_test_unified) from Salesforce documentation

---

### Apex Run 📟
🎮 `sf apex run` — Execute Apex Without the Dev Console

Have a quick Apex script you want to run? Don’t open the browser — just write it locally and run it via:  
**`sf apex run`**  

This will start the interactive mode. You can write the code want to execute, press Enter key after each line and Press CTRL+D when finished. This executes the code and will give you the log! 
    ![Image 8](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_8.png)
You can also execute the code from a `.apex` file using --file flag
**`sf apex run --file samplecode.apex`** 
    ![Image 9](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_9.png)
>📌Bonus Tip:  You can select apex code from any file, then open command palette(ctrl+shift+p) and select *>SFDX: Execute Anonymous Apex with Currently Selected Text* to execute the same anonymously and get log in Output tab.
>    ![Image 10](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_10.png)

>📚Do read more about [apex run](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_apex_commands_unified.htm#cli_reference_apex_run_unified) from Salesforce documentation

---
## 🔚 Wrapping Up
These 3 commands may seem small, but they seriously boost your productivity for sure. This saves time for opening your org and a lot of clicks.
If you’re an Apex dev and haven’t tried these yet — now’s the time. Once you start working from the CLI, it’s hard to go back.  
If you've got any other CLI favorites, feel free to drop them in the comments — always up for learning new tricks. ⚡ 
# Hope this helps fellow Apex devs out there save some clicks and stay in the flow 📈!!    
<div style="text-align: center;">

![Image 11](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p21_11.gif)

</div>

# What’s your favorite `sf` command? Do comment below📝!!!

