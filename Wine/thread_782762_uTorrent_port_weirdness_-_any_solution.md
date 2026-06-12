---
title: "uTorrent port weirdness - any solution?"
date: 2008-05-05
forum: Wine
---

### Post by Thanh-BKK on 2008-05-05
Hello :)

I am doing a lot of torrenting, mainly on private sites with ratio systems. 

Under Windows, i always used uTorrent - it's simply the best.

ut now i switched to Ubuntu - and i tried a number of clients, none is as good as uTorrent, mainly i miss the speed graph or (on Deluge, which i like otherwise) a "stop" button. If i can only pause a torrent, and the site's limit is 5 and i have 10 in que..... no way.

So i resorted to uTorrent in Wine - which works beautifully! But there is ONE issue.

I have forwarded port 60000 in the router for this purpose, and this works with all of the native apps.

However under Wine, it seems that ALL ports are open EXCEPT 60000!

So i chose another one - and after some time of uTorrent running, the network icon turns red again as now THAT port appears closed!

So in short, i am asking for a way to "teach" Wine to keep a certain port (ideally 60000) open at all times for uTorrent. Is this possible?

Remark: even if the port appears closed, up/downloading still goes at full steam (and faster than it ever did under Windows, i must add!) however the upload credit isn't reflected at the site once that port is closed. 

I am looking forward to a solution....

Kind regards......

Thanh

---

### Post by natrik on 2008-08-16
I have found this happening too.  I think perhaps there is a thread within utorrent that manages the listening port.  Maybe it spawns a new thread, but locks that port up for some reason.  Also, if I close utorrent, and open it back up too soon, my specified port will not be available.  My workaround was to change the port number for that session.  

(On my router, I have a range, say 50000-50500, forwarded to this specific computer.  I set aside some for utorrent, some for im's some for network services: ftp, smb, ssh, etc.)

A few minutes after changing the port number to another within that range, utorrent gave me the cheery green checkmark, and worked as expected.

Both with that alternate port, and on later occasions (after resuming my preferred port) I have noticed that little red icon in the status bar several more times, but it seems to self correct within a few minutes.

Wine: 1.1.2
utorrent: 1.8 (build 11813)

Oh, and the apt line for the wine repository (currentest version) is this:
**deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main**

In hardy, go to System > Administration > Software Sources.  In the tab "Third Party Software" click Add... and you can paste the above line.  Then you can click the Authentication tab to add the GPG file found at [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) -- this will authenticate your future downloads from this repository.

You can test the openness of local TCP port 60065 thusly:
```
telnet localhost 60065
```
if you get the following, it is open:
```
[B]Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.[/B]
```

then you do CTRL-] to get "telnet>" 
you can type "close", "quit", "bye" or hit ctrl-d to leave.

It may also say this, indicating the port is closed and unused:
```
[B]Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused[/B]
```

On the other hand if all you have is a blank line with the cursor at the first position, there is something bizzare, where the port is not unused, but it is also not acknowledging or accepting incoming connection attempts.  I don't know what you would want to do about that.

Of course, all this lets you know is the status of your LOCAL port, whether it is open, closed, or somehow locked up.  It does not mean that it is available to the internet.  But at that point it would be a forwarding issue, and not anything related to wine or utorrent.  

You can also use your local IP address instead of "localhost" in the telnet examples, useful if utorrent is only listening on a specified IP address, instead of the default of listening on all interfaces.

Hope all this helps!

Cheers,
Nate

---

### Post by Thanh-BKK on 2008-08-16
Hi :)

Thank you very much for the reply. I completely forgot this post as the problem kind of "fixed itself" and i have been using uTorrent ever since without further issues - i noticed however that when i "pause all torrents", then "resume all torrents" and the switch to "Logger" and back to "General", uTorrent will crash - very repeatable. And after it crashed (it will restart itself!) the port will be "closed" again until i reboot the computer, however downloading/seeding does still work. 

My Wine version is 1.0, in fact i just got this version a few days ago when i ran into a different problem (mp3trim, under Wine, refuses to open some of my mp3 files - but then opens some others, weird indeed!) and finally decided to allow my trusty Hardy to grab some of it's updates (as generally i HATE updating a perfectly running system), and Wine was among those. Nothing has changed though, everything works (or does not) just like with the older version.

Oh, and my uTorrent version is 1.7.7 - as i refuse to update THAT one, too :) 

To check whether a port is open i can use uTorrent itself - under "Options" and "Speed Guide" you can click "test if port is forwarded properly", a Firefox window will open and tell you if it's open or not. This works even when uTorrent runs under Wine. 

Before i start messing with Wine (i.e. the repo thing and updating), is there a difference between "my" version and even newer ones? If i understand correctly, the one i run is the latest on Ubuntu's repos. I tend to stick to things that work fine as often updates break more than they fix.......

With kind regards.....

Thanh

---

### Post by natrik on 2008-11-25
I was looking over some old posts I put up ...

uTorrent is constantly being improved, among other things, for compatibility with wine.  1.8.1 is proving very stable for me.   Occasionally when I have to restart it though, it doesn't want to use the same port over again.  Sometimes i have to kill wine and wait a few minutes.  

That's my only issue though.  Well, it would be nice to be able to re-organize the columns, like you can in windblows, but I can cope with that.

-- Nate

---

### Post by Thanh-BKK on 2008-11-25
Hi :)

I tried 1.8.1 but it wouldn't open torrents by double-clicking them - a well known problem with the 1.8.x versions under Wine.

I'm still using 1.7.7 and happy with it.... the crashing no longer happens, i guess one of Ubuntu's updates must have fixed something. 

Best regards....

Thanh

---

