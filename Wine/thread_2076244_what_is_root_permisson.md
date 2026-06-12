---
title: "what is root permisson?"
date: 2012-10-25
forum: Wine
---

### Post by vibaviattigala on 2012-10-25
so i am learning linux i heard of wine can run windows virus if i run wine with root whats that mean? how do i know if i just click wine apps whether its running root or not ?

i have installed wine with a sudo command if that is a superuserdo so i run the wine with root permisson so will my wine affected by virus?

---

### Post by danielbauwens on 2012-10-25
Root is like admin of a computer.

---

### Post by snowpine on 2012-10-25
Hi This cartoon explains how "sudo" works in Ubuntu:

[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

To answer your question, you must use "sudo" to install the Wine application because this is an administrative task on your system. You should not use "sudo" when you launch an application with Wine because this is an everyday user task, no special privileges required.

It is very unlikely that you would ever get a virus through Wine, I have not heard of this happening. (If you share files with Windows computers then it is possible you could pass along the infected file without realizing it or becoming infected yourself.) Here's a good introduction to security in Ubuntu: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Bucky Ball on 2012-10-25
_*Thread moved to **Wine***_


You might be advised to find out whether what you want to use works in Wine before you bother. Some things work great, others mediocre, many not at all. 

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If you install a cracked Win program with viruses into Wine then that's naughty! But beside that, the viruses would be written for Win. Not applicable. As Snowpine mentioned most sagely, though, you can pass these on to a Win machine.

If you intend using Win apps a lot I advise dual-booting or running a virtual machine ... ;)

---

### Post by arpanaut on 2012-10-25
Here's some information that you should be familiar with:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Unless you open wine with root privileges such as "gksudo wine" you should be okay.
I'm not a wine user so I don't know for sure, but windows programs being what they are, they are probably vulnerable to virus' so the wine program might be effected but the whole of your linux installation should not be vulnerable. (pure speculation on my part)
Might want to wait on a knowledgeable wine user.  My total experience with wine is to pop the cork and consume... lol

---

### Post by Stonecold1995 on 2012-10-28
Wine should never be run as root.  Not because of malware, but because it messes up the permissions and "breaks" Wine.  And yes, Wine can get infected with Windows malware, but usually it means the malicious software will be isolated in .wine, and even it tries to escape, it will be confined to your home directory (plus if it gets out, it won't be use to the Linux filesystem layout and will be "confused", i.e. it won't know what to do to mess up your computer or take control of it).  A lot of malware won't work under Wine however, if they try to use low-level tricks like buffer overflows it'll fail, but really simple malware might be able to infect Wine.

I have successfully gotten the remote administration trojan "DarkComet" to infect Wine, but it didn't have autostart capabilities, and it was limited to very simple abilities like creating and deleting files and opening windows, but it couldn't edit system settings, take screenshots, move the mouse, record webcams, etc.  Plus all its stealth capabilities were completely useless.

If you want to be even more secure, delete (or just move) .wine/dosdevices/z: (it's a symbolic link).  Removing that will make the rest of your computer "invisible" to malware.  Put it back when you want to be able to access the rest of your computer through Wine.

One thing I do when I want to run a program that might be malicious is I back up .wine and delete the link to z:.  You can do that by running this:
```
cp -r ~/.wine ~/wine-bak
rm ~/.wine/dosdevices/z:
wine possibly_malicious_program.exe
```
And if you want to undo any changes to .wine that the program may have made without your knowing, run this:
```
rm -r ~/.wine
mv ~/wine-bak ~/.wine
```

---

### Post by offgridguy on 2012-11-06
snowpine; luv your illustration

---

