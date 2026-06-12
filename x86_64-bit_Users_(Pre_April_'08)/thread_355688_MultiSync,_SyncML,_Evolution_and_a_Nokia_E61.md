---
title: "MultiSync, SyncML, Evolution and a Nokia E61"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mo_roodi on 2007-02-07
This is a bit of an off problem and I'm hoping someone can help! 

I have a Nokia E61 which I love - best smartphone ever - and I used to sync this with Microsoft Outlook via the Nokia PC Suite and supplied cable. 

I've since decided that Windows is in-fact rubbish and I've purged all systems of the evil... Everything's gone phone except that I now can't sync my phone (an annoyance more than anything).

Anyway yesterday I came across GSMSync.net - a free SyncML server. I thought I know what'll be a good idea, I can sync my phone with gsmsync and sync evolution through multisync with the SyncML plugin. I opted for this over the bluetooth option shown here [http://ubuntuforums.org/showthread.php?t=260676](http://ubuntuforums.org/showthread.php?t=260676) because I don't have a bluetooth dongle and don't really want/need one for my computer

I setup the GSMSync account, setup my phone and sync'd through my wireless network. So far so good. I installed multisync and the necessary plugins and tried to sync. Nothing! The log just says "connected to sync.gsmsync.net".

I've checked all the settings and made sure everything is setup correctly, checking obvious things like the URL and port and the database names, but alas no luck.

Can anyone suggest anything?

---

### Post by UCAP on 2007-02-13
> **mo_roodi said:**
> 
I have a Nokia E61 which I love - best smartphone ever


I'll have to agree with you :) 

I don't have any experience with GSMSync.net. I opted for scheduleworld.com and I haven't experienced any syncing problems whatsoever. I'm happily syncing Google Calendar, Evolution and E61. You might want to give scheduleworld.com a try.

---

### Post by Nanoelf on 2007-02-24
UCAP Please can you post how you synced the E61 with scheduleworld. What client did you use on the E61?

---

### Post by UCAP on 2007-03-03
Go to "Menu" on your E61, click on "Connectivity" and select "Sync". Once you are there select "Options", "New Sync Profile" (choose not to copy from "PCSuite").

1. Give the new profile a name (e.g. Scheduleworld)
2. Select "Applications"
    Click on Contacts, Calendar and Notes and choose to have them synched. For Contacts add    
    "card" as the remote database and do the same for Calendar (cal) as well as Notes (note).
3. Go back and click on Connection settings.
[LIST]
[*] Server version: 1.2
[*] Server ID: funambol
[*] Data bearer: Internet
[*] Access point: *choose your access point*
[*] Host address: [http://sync.scheduleworld.com/funambol/ds](http://sync.scheduleworld.com/funambol/ds)
[*] Port: 80
[*] Add your scheduleworld.com username and password
[/LIST]
4. Go back to "Sync" and click on your newly created profile and confirm that you want to sync  - that's it. Happy synching ;-)

---

### Post by RCookson on 2007-03-05
Hi, I've set up my E61 with Scheduleworld as you suggest. It works, but not properly! I can download the data in one direction, but if I try a two way sync it just locks up and eventually times out with a "server not responding" message. When I looked on the Scheduleworld forums I found other E61 users had reported similar problems when connecting via MMS. The problems apparently didn't occur if they connected by WLAN? I was wondering what connection you were using to get syncing to work properly, do I need to connect via WLAN do you think?

---

### Post by UCAP on 2007-03-05
I can sync in both directions. I don't normally use WLAN to connect but a WAP (GPRS) connection and never experienced any problems so far (except, of course, when scheduleworld.com is down which happens occassionally).

---

