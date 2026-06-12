---
title: "How Soon?"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angelbeast on 2007-05-21
How soon yet before java goes open source and works with 64 bit firefox?

I know about blackdown but frostwire doesn't work with it.

---

### Post by sharke on 2007-05-21
I have black down jre installed for browser and java 6 for aplications works well with frostwire.
Regards
Sharke

---

### Post by Angelbeast on 2007-05-21
> **sharke said:**
> I have black down jre installed for browser and java 6 for aplications works well with frostwire.
Regards
Sharke

you got both to work?? i tried to do that but it was making things crash...how did you get it to work?

---

### Post by Angelbeast on 2007-05-21
okay so now its making a liar out of me *LOL* ... it's working now but i'm not getting any sound on Pogo...

---

### Post by Angelbeast on 2007-05-21
okay looks like i'm lying again...it started crashing again so i uninstalled blackdown.  You said you had both installed and working? What verion of Java? All i saw in dd/remove was Web Start 6
and jre 5

---

### Post by sharke on 2007-05-21
I installed blackdown jre from the repos with synaptic and then frostwire with Automatix which installs java as a dependency. I an busy with work at moment but will test pogo for you.
Regards
Sharke

---

### Post by kuja on 2007-05-21
I think it's the Java 7 tree that is opened, but it's hard to tell when it will be finished. Just because it's open source doesn't mean it'll have a working x86_64 netscape plugin; that will probably take more time.

---

### Post by Angelbeast on 2007-05-22
> **sharke said:**
> I installed blackdown jre from the repos with synaptic and then frostwire with Automatix which installs java as a dependency. I an busy with work at moment but will test pogo for you.
Regards
Sharke

did it crash for you too?

---

### Post by kleeman on 2007-05-22
I have java working in firefox without issues but I use gcj instead of blackdown. Try this:

sudo apt-get install gcjwebplugin-4.1

sudo cp /usr/lib/gcj-4.1/libgcjwebplugin.* /usr/lib/mozilla/plugins

---

### Post by Angelbeast on 2007-05-22
> **kleeman said:**
> I have java working in firefox without issues but I use gcj instead of blackdown. Try this:

sudo apt-get install gcjwebplugin-4.1

sudo cp /usr/lib/gcj-4.1/libgcjwebplugin.* /usr/lib/mozilla/plugins

I'm willing to try it but if it doesn't work how would i uninstall it?

---

### Post by kleeman on 2007-05-22
> **Angelbeast said:**
> I'm willing to try it but if it doesn't work how would i uninstall it?

sudo apt-get  remove gcjwebplugin-4.1

sudo rm /usr/lib/gcj-4.1/libgcjwebplugin.* /usr/lib/mozilla/plugins

---

### Post by Angelbeast on 2007-05-23
> **kleeman said:**
> sudo apt-get  remove gcjwebplugin-4.1

sudo rm /usr/lib/gcj-4.1/libgcjwebplugin.* /usr/lib/mozilla/plugins

okay i tried it and on pogo i got a dialog that asked if iwanted to dd the applet to a whitelit so i did. then the pop up for the gme closed and then igot this error...
> 
The following error has occurred:
Java Not Found or Not Working

Explanation:
This error means Java (one of the technologies built into most browsers) is not working correctly on your browser.

You must have Java installed on your computer in order to run Pogo games, and it must be functioning properly. Either you don't have Java installed yet, or the Web browser you're currently using doesn't support Java or you have Java (or Javascript) disabled in your browser.

if there awork around for this with whatyou recommended? :-)

---

### Post by kuja on 2007-05-23
Probably easiest to use a 32-bit browser with the 32-bit plugin (from the ia32-sun-java6-bin package). Should work without any trouble.

---

### Post by kleeman on 2007-05-23
Yeah that site did not work for me either. Many others do e.g. the dslreports speedtest.
The firefox32 browser with java works however....

---

### Post by Angelbeast on 2007-05-23
> **kleeman said:**
> Yeah that site did not work for me either. Many others do e.g. the dslreports speedtest.
The firefox32 browser with java works however....

well i guess that's my only choice then...so will the 32 bit firefox install OVER the 64 bit one without me having to ess with tranfering  or backing up and restoring y profile and everything?

---

### Post by kleeman on 2007-05-23
Check out Kilz's instructions here:

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

It coexists with the 64bit version easily.

---

### Post by Angelbeast on 2007-05-24
> **kleeman said:**
> Check out Kilz's instructions here:

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

It coexists with the 64bit version easily.

now with this which one will register at the default one? i mean will the 32 bit one open on it's own when i click on web shortcut and so on?

---

### Post by kleeman on 2007-05-24
> **Angelbeast said:**
> now with this which one will register at the default one? i mean will the 32 bit one open on it's own when i click on web shortcut and so on?
The 64bit stays as the default perhaps because it is the official package and/or Kilz did not switch the default settings with his package..

---

