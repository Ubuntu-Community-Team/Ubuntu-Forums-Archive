---
title: "LogMeIn Firefox 3 Addon"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by TC10284 on 2008-06-17
Hey guys, 
  
 Has anyone tried to use the LogMeIn Firefox 3 extension in Hardy Heron 64bit? 
  
 Each time I try to connect remotely, it doesn't seem to work properly. The only thing I can get is LogMeIn refreshing what looks to be an image of the remote desktop that's not interactive. Each time you click the image, it refreshes the screen, but you can't do anything with it. 
  
 LogMeIn's site doesn't ask me to install the extension either. I had to search Google for "logmein Firefox" to get to the extension install page. But I still had no luck. I've removed it, reinstalled it, but no dice. =( 
  
 Anyone got it to work?

---

### Post by Kilz on 2008-06-17
> **TC10284 said:**
> Hey guys, 
  
 Has anyone tried to use the LogMeIn Firefox 3 extension in Hardy Heron 64bit? 
  
 Each time I try to connect remotely, it doesn't seem to work properly. The only thing I can get is LogMeIn refreshing what looks to be an image of the remote desktop that's not interactive. Each time you click the image, it refreshes the screen, but you can't do anything with it. 
  
 LogMeIn's site doesn't ask me to install the extension either. I had to search Google for "logmein Firefox" to get to the extension install page. But I still had no luck. I've removed it, reinstalled it, but no dice. =( 
  
 Anyone got it to work?

You may have better luck [contacting LogMeIn directly]("https://secure.logmein.com/home.asp") for support. Since its a commercial product they should help you if you paid for it.

---

### Post by wolfe on 2008-06-17
there is a free version of this app as well.  But I have been under the impression you can only use it on windows.  I know they recently added support for connecting to macs, but I dont think there is currently any support for linux in either direction.  I'd love to be proven wrong though.

---

### Post by TC10284 on 2008-06-17
> **wolfe said:**
> there is a free version of this app as well.  But I have been under the impression you can only use it on windows.  I know they recently added support for connecting to macs, but I dont think there is currently any support for linux in either direction.  I'd love to be proven wrong though.

They do have a free version of LogMeIn. Also, there is no current public Linux "server" version of LogMeIn. You can only connect remotely to Windows PCs (sigh) from Linux. I'm just using their browser extension on Hardy Heron to connect to my desktop back home. I've used the LogMeIn Firefox Extension in FF3 on a 32bit version of Hardy Heron with no problems. That's why I'm asking here too (other than the LogMeIn forums).   

Also, I'm willing to bet someone is going to ask me why I'm not using VNC, well, I've used all those before, and they're nice, really nice. I just don't want any open ports on my firewall unless I absolutely have to. LogMeIn doesn't require any open ports.

---

### Post by Kilz on 2008-06-17
> **TC10284 said:**
> They do have a free version of LogMeIn. Also, there is no current public Linux "server" version of LogMeIn. You can only connect remotely to Windows PCs (sigh) from Linux. I'm just using their browser extension on Hardy Heron to connect to my desktop back home. I've used the LogMeIn Firefox Extension in FF3 on a 32bit version of Hardy Heron with no problems. That's why I'm asking here too (other than the LogMeIn forums).   

Also, I'm willing to bet someone is going to ask me why I'm not using VNC, well, I've used all those before, and they're nice, really nice. I just don't want any open ports on my firewall unless I absolutely have to. LogMeIn doesn't require any open ports.

If you extension worked on 32bit Hardy. Perhaps its a 32/64bit problem. Sometimes extensions need to be the same bit as the browser. If there isnt a 64bit version of the extension perhaps[ you might install a 32bit browser.]("http://http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by TC10284 on 2008-06-26
Your script worked excellently! The LogMeIn client works wonderful now!

---

### Post by DoomedTX on 2008-08-23
I'd like to point out for clarity's sake that as far as I can tell, the Logmein FF 3.0 extension does not work in any version of Ubuntu.

What does work is the Java applet that Logmein falls back on in case ActiveX and the Mozilla plugin are not detected. While using the Java applet provides essentially equal functionality, it is not identical.

My biggest beef with the Java applet, BTW, is that it disconnects every time you change tabs and causes you to wait for a new connection when you come back to the tab. The plugin version, at least on Windows and Mac machines, does not experience this Java-related nuisance.

---

### Post by johnnylavah on 2008-08-24
> **TC10284 said:**
> Hey guys, 
  
 Has anyone tried to use the LogMeIn Firefox 3 extension in Hardy Heron 64bit? 
  
 Each time I try to connect remotely, it doesn't seem to work properly. The only thing I can get is LogMeIn refreshing what looks to be an image of the remote desktop that's not interactive. Each time you click the image, it refreshes the screen, but you can't do anything with it. 
  
 LogMeIn's site doesn't ask me to install the extension either. I had to search Google for "logmein Firefox" to get to the extension install page. But I still had no luck. I've removed it, reinstalled it, but no dice. =( 
  
 Anyone got it to work?

have you tried installing sun java and then changing the logmein preferences to use java instead of mozilla plugin, active x, etc... to connect?

---

### Post by TC10284 on 2008-11-10
I've found recently that after upgrading the 32bit install of Firefox for Ubuntu x64, that I can no longer connect remotely using LogMeIn.

Anyone else having trouble or have a solution?

---

### Post by johnnylavah on 2008-11-11
> **TC10284 said:**
> I've found recently that after upgrading the 32bit install of Firefox for Ubuntu x64, that I can no longer connect remotely using LogMeIn.

Anyone else having trouble or have a solution?

sometimes when i use logmein on windows it switches java back to activex in preferences...maybe this is happening to you?

---

