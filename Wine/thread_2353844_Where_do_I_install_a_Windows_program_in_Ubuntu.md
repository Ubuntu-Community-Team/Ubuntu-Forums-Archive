---
title: "Where do I install a Windows program in Ubuntu"
date: 2017-02-25
forum: Wine
---

### Post by helium2 on 2017-02-25
My knowledge of Ubuntu is 4 days old but so far I find it works well.
I have Ubuntu 16.04 installed on an SSD drive and Win10 on another SSD drive. I have a large data drive that both Operating systems can access. I can dual boot Ubuntu and WIn10 and all works well. I have installed Wine as I wish to install some Windows apps. When I click the Appxx .exe that I wish to install, it indicates a default path of C:\Programs which is the WIn10 SSD. I wish to install to the Ubuntu SSD. Assuming I can install to the Ubuntu SSD which folder do I install in and do I need to set permissions? I am trying to avoid installing anything to the Win10 drive.

---

### Post by Perfect Storm on 2017-02-25
When you use wine to install windows programs with, it set up a fake C:\ it actually installs it under your hidden folder .wine in your home directory.

---

### Post by howefield on 2017-02-25
and moved to the "*Wine*" forum.

---

### Post by helium2 on 2017-02-25
Thanks I see what you mean now, so I have attempted to install a few apps, some appear to install but do not run without problems of various kinds. Paintshop Pro (several versions various issues, none get as far as opening the actual program)  and Breezebrowser  opens but does not show any directories. I will try some other apps

---

### Post by howefield on 2017-02-25
Many applications are rated at the [winehq database]("https://appdb.winehq.org/") although some ratings may be few in number and old in nature, it is still worth having a look.

---

### Post by Perfect Storm on 2017-02-25
helium2, why not find alternative to the applications you use in windows?

---

### Post by helium2 on 2017-02-25
> **Artificial Intelligence said:**
> helium2, why not find alternative to the applications you use in windows?

I have used Breezebrowser for over 10 years and find it much faster for Canon files ra file browsing than anything else. I have tried all the others every few years but nothing browses as fast.
I have tried adding the two DLLs that some have found get it going but as I am new to linux I am not sure I have them in the right place. I did put them in the Breezebrowser directory and also in wine but no go so far.

---

### Post by Perfect Storm on 2017-02-25
I don't use wine so I can't say - but there's a good read about setting dlls in wine here: [https://www.winehq.org/docs/wineusr-guide/config-wine-main](https://www.winehq.org/docs/wineusr-guide/config-wine-main)

---

