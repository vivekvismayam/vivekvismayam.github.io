# Setting Up A Telegram-Powered Media Downloader📲 for My Home Lab Using Node.js🔋

# Have you thought of Turning Telegram into a Remote Media Pipeline for your Home Server??🚀
## 🔍 Background
Managing media in a home server setup can be both fun and challenging—especially when you're trying to automate file ingestion into services like [Jellyfin](https://jellyfin.org/) or [Plex](https://www.plex.tv/media-server-downloads/). 
Recently, I started setting up a home lab server using one of my old laptops.  Initially, I relied on [qBittorrent](https://www.qbittorrent.org/) and [Aria2 with AriaNG](https://hub.docker.com/r/hurlenko/aria2-ariang) to download files for my personal Jellyfin Service. However, finding the right content via torrents was often challenging.Telegram, on the other hand, makes it incredibly easy to discover and share files. But downloading those files directly to a server isn’t straightforward — at least, not out of the box.
I wanted a way to send videos or movies directly from my phone into my home lab server over Telegram, without needing to log in via SSH or set up web UIs for upload.

My first instinct was to use a **Telegram bot**, but I quickly hit a few roadblocks:

* Telegram bots running on a public server have a 50MB file size limit when using the getFile method, making them unsuitable for downloading large video files.
* Most Telegram bot libraries designed for local server setups are typically written in Python, which isn’t my strongest area — so I began looking for a Node.js alternative.
* Bots usually require public endpoints or tunneling to work properly with webhooks, adding complexity to a local setup.

That’s when I discovered [**GramJS**](https://github.com/gram-js/gramjs), a Telegram MTProto client for **Node.js**. It allowed me to use my preferred tech stack to build a flexible and fully offline-compatible solution.

---
## 🧠 The Idea
The concept is simple:  
1. Run a **Telegram client** on my **Ubuntu-based home server**, logged in with one of my own Telegram accounts.
2. Forward video files or movies to this logged in account from my main Telegram account.
3. The client listens for **new messages** from **only me** and downloads the media to the appropriate folder.
4. The files are routed based on **keywords** (e.g., `#movie`, `#series`) and ingested by **Jellyfin**.
5. I also get **real-time progress updates** and control the system via chat commands.

---
## ⚙️ Key Features
### ✅ Runs on Node.js, Not Python  
To avoid Python-based tooling, I built this using `gramjs` in Node.js. This allowed me to work within my comfort zone and avoid maintaining a secondary Python setup.  
### 🔐 Private and User-Filtered  
The downloader only processes messages from **my personal Telegram account**. Any other messages or forwarded content from other users are ignored for security and simplicity.  
### ♻️ No Duplication
The Telegram client processes **only fresh messages** as they arrive. It doesn't go back to previous messages or attempt re-downloads. This keeps storage clean and avoids accidental duplication.
### 🟢 Startup Notifications
![Image 0](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p20_4.png)
Every time the program restarts, I get a message on Telegram saying: *👀 Listening for new messages...*  
This helps ensure that even after a reboot or crash, free logging and I know the service is alive and behaving correctly.
### 📊 Real-Time Download Progress
I've added logic to **track and report download progress** back to me on Telegram:
* Every 10% completion triggers a new message (*"Download crossed 20%"*) quoting the original file.
* Yes, Telegram allows you to edit a single message to update progress, but I intentionally chose **separate progress messages** for now — it helps me monitor performance, especially during the early phases of usage.
![Image 1](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p20_1.png)
### 📁 Keyword-Based Download Routing
Based on specific **keywords in the message text**, the download path is selected dynamically:
* Send a message `Path` to check which path is currently active- Movie (`/home/media/movies`) Or Series(`/home/media/series`)
* Send a message `ChangePath` in the Telegram chat to toggle the path between configurable Paths- Movies & Series.  
This categorization feeds directly into Jellyfin’s folder-based library scan and gives me a quick way to control the system remotely without touching the server terminal.
![Image 2](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p20_2.png)
### 🔄 systemd Service for Background Execution
To make sure the script runs **reliably in the background**, I created a `systemd` service for Ubuntu.
This ensures
* Automatically **starts on boot**
* Restarts automatically on failure
* Runs independently of any terminal or SSH session
* Easy to manage via `systemctl` commands

---
## 📦 How To Setup This?
You can find the code and feel free if you want to set up the same [TelegramClientDownloader](https://github.com/vivekvismayam/TelegramClientDownloader) 
Please find below for detailes setup instructions.
1. Clone this Reporitory: [TelegramClientDownloader](https://github.com/vivekvismayam/TelegramClientDownloader) 
2. Run `npm Install`
3. Set up environment variables
```.env
    #Replace API ID and Hash with your values from https://my.telegram.org/auth
    TELEGRAM_API_ID=0000
    TELEGRAM_API_HASH=123456789

    #Download files only if forwarded from below user
    ADMIN_USERNAME=@username

    #Remember to keep \ or/ at the end as per platform
    MOVIES_DOWNLOADPATH= #your movies download path Eg: /Shared/Jellyfin/Movies
    SERIES_DOWNLOADPATH= #your series download path Eg: /Shared/Jellyfin/Series

    #Keep DELETE if you want to delete message(file) from chat post download. Case Sensitive. Any other file will avoid file from getting deleted from chat
    DELETE_FILES_POST_DOWNLOAD=DELETE

```
>⛔ Do not expose your Telegram API ID Or API Hash. Store these securely!  
>✳️Steps for [Creating your API Id and Hash](https://core.telegram.org/api/obtaining_api_id)
4. Run `npm run listen`
5. Authenticate with Phone number and 2F Auth code(Refer [Gram JS](https://gram.js.org/) for more details on auth)
**Create a Service File in Ubuntu**
If you want to run as a service file in ubuntu, follow below steps:
1. Create a service file 
```bash
sudo nano /etc/systemd/system/telegram-client.service
```
>Sample Service File
>```ini
>[Unit]
>Description=Telegram Media Downloader
>After=network.target
>
>[Service]
>ExecStart=/usr/bin/node npm run listen
>Restart=on-failure
>User=youruser
>Environment=NODE_ENV=production
>WorkingDirectory=your working directory
># Optional logs
>StandardOutput=append:/var/log/telegram-client.log
>StandardError=append:/var/log/telegram-client-error.log
>
>[Install]
>WantedBy=multi-user.target
>```

>Learn More  
>[Understanding Systemd Units and Unit Files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
2. Start and enable:
```bash
sudo systemctl daemon-reload
sudo systemctl enable telegram-client
sudo systemctl start telegram-client
```
3. Check status:
```bash
sudo systemctl status telegram-client
```
![Image 3](https://raw.githubusercontent.com/vivekvismayam/blog-assets-1/refs/heads/main/Images/p20_3.png)
> Learn more  
> [Manage Systemd Services with systemctl on Linux](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

---
## 📉 Limitations
* Telegram media links are temporary — if the download is too slow, it may expire.
* No retry logic yet for failed downloads (planned).
* Currently supports only one user — multi-user control is possible but not implemented intentionally for simplicity and safety.

---
## ✅ Why I Love This Setup

* 100% automated — just forward a video and it’s in Jellyfin within minutes.
* No need to manually upload, share, or mount folders.
* Secure, private, and self-hosted.
* Real-time feedback keeps me confident it’s working.

---
## 🙌 Final Thoughts

This Telegram + Node.js + GramJS automation has been a game-changer for managing media on my home lab. If you're comfortable with Node.js and Telegram, this is a simple yet powerful workflow you can set up cloning the github repo in few minutes.  
Even if you don’t have a dedicated home server, you can still use this setup to remotely download files to your desktop or laptop via Telegram — perfect for grabbing a few files while you're away.  

*Do comment below if you have have a better idea or implemented something similar!*
