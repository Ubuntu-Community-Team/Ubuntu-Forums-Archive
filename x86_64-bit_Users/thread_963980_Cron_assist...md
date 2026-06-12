---
title: "Cron assist.."
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by HarshReality on 2008-10-30
So, what I am trying to do is cron a php file and have it upload to my site (overwriting it if it exists) and then delete the local.

Trick is what Im wanting written to the file.. trying to get it to post..
(font and specific formatting variables) uptime then kernel, CPU usage & upload and downloads for the month (I have vnstat for that info) each on a new line.. any ideas here guys? Ive tried using a script and echo > filename but that isnt worth squat.

---

### Post by bve on 2008-10-31
It's not really clear what you are trying to do.

Is it that you want to run a php script to gather information from your system (or a remote system) and upload the results?

Do you have the data capture solved and just want to post the information remotely? If so what protocol(s) are available on the server to recieve it - ftp, http, ssh?

---

### Post by HarshReality on 2008-10-31
> **bve said:**
> It's not really clear what you are trying to do.

Is it that you want to run a php script to gather information from your system (or a remote system) and upload the results?

Do you have the data capture solved and just want to post the information remotely? If so what protocol(s) are available on the server to recieve it - ftp, http, ssh?
Your correct, I want to capture system data, export it to txt with variables and upload it as a php file via FTP.

---

### Post by bve on 2008-10-31
What part of all of this have you finished already?

1) Do you have your system data from VMSTAT already in the text file?

2) Is there any further data processing to take place on the server or will the data be static after uploading? If it is static then there is no need for the file to be php it could just be html - more clarity needed.

3) scp or sftp is more secure than ftp and can be done using public/private keys rather than storing your password in plain text in a script. Do you have ssh/shell access to the server or only ftp?

4) Cron just runs a command at specific time as per your settings in your crontab, do you already know what you need there or is that the only part of this you need help with?

As mentioned earlier you need to be much more specific as to what you have done already and what part of this you need help with.


Burke

---

### Post by HarshReality on 2008-11-01
Well, cron is simple enough, I suppose what I need help with would be the script. As for specific.. its really hard to be much more than what I already stated.. if I could be more specific than that I'd have it in script form and already be doing it.

Somebody close this thread or remove it or something.. I Was hoping for a simple syntax example to attempt to export and then modify myself to suit but its clearly not going to go that way... As such I wont waste anymore of anybody's time.

---

### Post by bve on 2008-11-02
> **HarshReality said:**
> Well, cron is simple enough, I suppose what I need help with would be the script. As for specific.. its really hard to be much more than what I already stated.. if I could be more specific than that I'd have it in script form and already be doing it.

Somebody close this thread or remove it or something.. I Was hoping for a simple syntax example to attempt to export and then modify myself to suit but its clearly not going to go that way... As such I wont waste anymore of anybody's time.

What's clear to me is you couldn't make the small effort to answer my questions so someone could help you, if you had answered them you would have made things clearer and got your example - in other words I or someone else would have known where to start.

This puts the output into a text file.
```
vmstat > vmstat.txt
```

[Bash Guide](http://www.gnu.org/software/bash/manual/html_node/index.html)
[Bash Howto](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[scp examples](http://www.hypexr.org/linux_scp_help.php)

Good luck.

---

