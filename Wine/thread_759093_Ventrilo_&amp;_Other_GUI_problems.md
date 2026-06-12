---
title: "Ventrilo &amp; Other GUI problems"
date: 2008-04-18
forum: Wine
---

### Post by spacecataz on 2008-04-18
Now all of you are probably tired of seeing all these ventrilo threads, but my problem is not just limited to vent.

Every time I start up some type of GUI launcher, whether it be Ventrilo or an install for some game, certain buttons and/or text/drop down boxes are grey'd out and/or invisible.

This may be a complete beginner question, but as an ubuntu beginner, is there any way i can fix this?

By the way, when i open vent, this is what my screen looks like:
[http://img241.imageshack.us/my.php?image=screenshotventriloge3.png](http://img241.imageshack.us/my.php?image=screenshotventriloge3.png)

---

### Post by FrozenFox on 2008-04-18
Ventrilo works pretty much flawlessly for me on ubuntu or arch, wine 0.9.59, and has worked well on ubuntu for as long as I can remember. There must be some issue with your setup here, so let's try a few things..

Where did you get wine? From the official ubuntu repositories or did you get wine from winehq.com or somewhere else?

Try deleting /home/YOURNAME/.wine  (note that it's a hidden folder by default, hence the dot, so enable your file manager to view hidden files in the settings), then reinstalling again via following the directions from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) . If you use hardy, I think the directions for gutsy will work ok, but I'm not completely sure.

When you get done with that you should have wine version 0.9.59 installed. You can check this via typing wine --version in the terminal / console. Try vent again and tell us how it went. If this still fails, please run your program from the terminal (in this case, ventrilo) and give us the output the terminal gives you, via wine /path/to/ventrilo/ventrilo.exe.

If indeed that turns out to fix your problem, you may want to try a script I posted a ways back after installing wine 0.9.59 because it installs vent & enables such stuff as text-to-speech, [http://ubuntuforums.org/showthread.php?t=686256](http://ubuntuforums.org/showthread.php?t=686256) . However, I'd suggest trying to get a normal install to actually show up first before spending the time to look at that.

---

### Post by spacecataz on 2008-04-18
I checked the version i have, and it is the most current version out there.

when i ran vent from the terminal, this came along with it:

> 
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered


---

### Post by spacecataz on 2008-04-18
rest of it:

> err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17

---

### Post by FrozenFox on 2008-04-19
Odd, I get the same things as far as I can tell and vent runs ok. You're not having problems with any other windows but wine-related stuff drawing correctly, right? If so, please try deleting the aforementioned /home/yourname/.wine and reinstalling both wine and vent via the winehq instructions and tell us if that changes anything.

---

