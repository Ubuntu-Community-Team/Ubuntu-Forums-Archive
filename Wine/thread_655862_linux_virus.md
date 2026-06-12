---
title: "linux virus"
date: 2008-01-01
forum: Wine
---

### Post by manchu99 on 2008-01-01
a friend of mine emailed me a little program. i tried it on my linux machine with wine and it worked. later i used it on a windows computer, and the anti-virus program told me it was infected. After i cleaned the xp computer, i got to wondering if i need to be worried about a trojan virus messing with my linux box on which i ran that program. I looked for the registry entries in wine that xp told me were infections on that other computer but found nothing. Do i need to worry?

---

### Post by delphiguy on 2008-01-01
cheers you need not worry about viruses in linux.  
if you are indeed worried about viruses in linux, you can install clamav
and the nice gui frontend for it Klamav.

---

### Post by dasunst3r on 2008-01-01
Tell us more about the "trojan" your friend wrote.  What does it do?  How did it function?  It is also important to note that WINE ignores startup programs and is not called unless you manually invoke a program file.  Therefore, the success rate of a virus hurting anything beyond your home directory is not very high.

---

### Post by manchu99 on 2008-01-02
he didn't write it, merely passed it along without knowing better.. i guess. the antivirus program called it trojan.caiijing and soon after said it found w32.ircbot

---

### Post by pdub on 2008-01-06
As a test, I ran a program that contains the Bagle-8 worm using Wine on Ubuntu 7.10 Gutsy.

After executing the file, a ps -A reveals the following:

 8908 ?        00:00:05 notification-da
11301 ?        00:00:01 pdflush
[COLOR="Red"]11512 ?        00:00:02 ~14a3.exe
11515 ?        00:00:00 explorer.exe[/COLOR]
28901 ?        00:00:00 scsi_eh_12
28902 ?        00:00:00 usb-storage
28944 ?        00:00:00 hald-addon-stor

You can see the worm running as ~14a3.exe

I used ClamAV to scan the Wine file system:

./.wine/drive_c/windows/system32/hldrrr.exe: Worm.Bagle-8 [COLOR="Red"]FOUND[/COLOR]

./.wine/drive_c/windows/temp/~14a3.exe: Worm.Bagle-8 [COLOR="Red"]FOUND[/COLOR]

The Worm did not survive a reboot but it seems reasonable to conclude that certain malware will execute under Wine.

---

### Post by LaRoza on 2008-01-06
> **pdub said:**
> 
The Worm did not survive a reboot but it seems reasonable to conclude that certain malware will execute under Wine.

It may execute, but it can't do much. There is no registry to mess with, the directory hierarchy is different, and you have limted rights.

---

### Post by simplyw00x on 2008-01-06
There was an humorous article testing virus compatability with wine a while back (search for it...). Although there are none yet, remember that it;s trivial to write a "virus" that deletes all user data and configuration, so perhaps linux is *more* vulnerable in this regard, as few people have clamav installed. The only hurdle in a linux virus is having it download and execute silently, and this could be done with a browser bug (of which firefox has several, though none this major last long).

---

### Post by stzasnail on 2008-01-06
Don't worry. If you have not heard all of the ranting and raving from fanboys, one of the huge draws to Linux is the lack of viruses. If you really want to feel more secure, you could install CalmAV and Firestarter (although I have been informed that Ubuntu comes by default with all ICP/TCP ports closed except for the internet access port therefor making a firewall a fallback)

PS: Please correct me if I am wrong on this.

---

### Post by julian67 on 2008-01-06
> **stzasnail said:**
> Don't worry. If you have not heard all of the ranting and raving from fanboys, one of the huge draws to Linux is the lack of viruses. If you really want to feel more secure, you could install CalmAV and Firestarter (although I have been informed that Ubuntu comes by default with all ICP/TCP ports closed except for the internet access port therefor making a firewall a fallback)

PS: Please correct me if I am wrong on this.

OK, correction :)

Ubuntu and all Linux distros using recent kernels include iptables, which can be used to act as a packet filtering firewall. In Ubuntu out of the box there are zero restrictions, all connections in and out are allowed, the ports are not closed. However, by default there are* no services listening*,  so your exposure to unwanted connections is low. But as soon as you are running an application or daemon/service that listens (examples: any p2p application, ssh server, samba server, dhcp server etc) you are visible and need to seriously consider using a firewall because at this point your security is completely relying on your services/applications having no vulnerabilities and your password(s) being very strong.  Even using a web browser such as Firefox can lead to trouble....all those cooool extensions! Who wrote them? What do they actually do? Where are they from? Are they open source? Is anyone actually bug fixing them? What are they linking you to? And Firefox itself (and any web browser) inevitably has vulnerabilities. Generally it's safer to browse from Linux than Windows because at least on Linux you are using an account protected with a password and with limited privileges and most nasty stuff like cross site scripting attacks and silent malware installs are targeted solely at Windows, but there are plenty of people/bots out there which will hammer away with dictionary attacks on your user names and passwords if they know you're there and can see you have some services listening.  Fortunately your router provides a good firewall, so secure/configure that and password protect it. You don't really need to worry about viruses but it's conceivable that a wine install with a Win virus might cause some problems with your /home partition or folder (though I've never heard of this, anyone else?), which after all is the one we value the most as users, but there is no real danger afaik of your system being affected by a Win virus in your .wine folder because even if it were written to exploit Linux rather than Windows you would have to explicitly execute it with sudo.  Unless you're running a mailserver I wouldn't consider installing any kind of AV on Ubuntu, it doesn't offer any extra protection for you, or anyone you connect with who uses Windows and has their own AV.   But a firewall is more fundamental and will offer you more protection in most circumstances than Ubuntu's unconfigured iptables status can.  Firestarter is an easy to use front end to iptables and available via Synaptic and will seem reasonably simple to anyone who has used some of the Windows personal firewalls.  It's worth installing it just to have easy gui access to the firewall logs...it can make surprising reading!

---

### Post by cherva on 2008-01-06
If someone is scared by a windows virus witch can make some BAD stuff in your /home/<USERNAME>  with the help of wine. Why don't you make another user account and run the wine stuff from it ? This way no data from your real home can be harmed.

---

### Post by matchstich on 2008-01-06
> **delphiguy said:**
> cheers you need not worry about viruses in linux.  
if you are indeed worried about viruses in linux, you can install clamav
and the nice gui frontend for it Klamav.

installed both of these.  but where did they go?

can not find them  on main menu.

thanks

---

### Post by handy on 2008-01-07
The following link is old but perfectly valid for understanding viruses on Linux, Mac OS X & Windows:

***_[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)_***

---

### Post by BenniP on 2008-01-09
> **matchstich said:**
> installed both of these.  but where did they go?

can not find them  on main menu.

thanks

You can add the Frontend to the Menu (in System > Pref > Main Menu), you just have to know the name of the binary - which is **klamav** in this case.

In general, you have to do some intelligent guessing, or you consult the list of installed files of the package installed (in the properties menu of the package in Synaptics).

---

### Post by matchstich on 2008-01-10
thanks for the info.

read another thread about clamtk.  installed it and 

every thing is good. the gui showed up in accessories.

---

