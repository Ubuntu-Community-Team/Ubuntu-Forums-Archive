---
title: "if i opena installer w\ virus in wine is my computer will be infected?"
date: 2008-07-27
forum: Wine
---

### Post by xnostradamusx on 2008-07-27
i read some that dont use wine as a root user but i have no idea if i am opening some windows applications and there might be a spyware or virus
bundled with it.

can anyone shed some light to me pls? now im worried and installed clam av
and firestarter because i think i might be infected

---

### Post by qbox on 2008-07-27
Hi.
Nice question. And I want to know the answer..:confused:

---

### Post by Joeb454 on 2008-07-27
I doubt it. I think the most damage it would do would be to trash your Wine installation

---

### Post by Martje_001 on 2008-07-27
Firestarter is NOT A FIREWALL. It's only a front-end to the already-installed iptables.

Secondly, yes you can be affected. But if you don't run it as root it can only delete (that's absolutely the worst it can do) the content of your home-folder.

Next time search btw:
[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)
[http://ubuntuforums.org/showthread.php?t=471499](http://ubuntuforums.org/showthread.php?t=471499)
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by Martje_001 on 2008-07-27
> **Joeb454 said:**
> I doubt it. I think the most damage it would do would be to trash your Wine installation
Maybe, but if you have setup your drives through winecfg..

---

### Post by forger on 2008-07-27
You can easily remove the badware if it managed to be installed in wine (which is not likely to happen). Think of wine as a REALLY slimmed down version, in which a lot of registry info for badware are missing :)

You can check out if something is indeed using a connection to the internet:
1) Open applications > accessories > terminal (maximize the window for better view)
2) close all your internet-related applications (i.e. internet browser firefox) and wait for 5 minutes. This is in order to get a clearer view of your connections
2) execute: ```
sudo netstat -ap | grep -i "tcp\|udp"
```
this command will show you all the outgoing connections 
3) check out weird connections 

You can kill all your wine applications with a single command:
```
wineserver -k
```
This command will kill *all* applications that use wine :)

You can also simply remove wine home directory:
1) Open applications > accessories > terminal
2) **[COLOR="Red"]WARNING! Will lose all your wine-related configuration files![/COLOR]** (but sometimes this is necessary in cases of emergency such as virus infection)
Execute: ```
wineserver -k
rm -rf $HOME/.wine
winecfg
```
These commands will kill the wine server and remove your .wine folder in your home directory. Then it will regenerate a new (default and clean) wine configuration for you - you simply click Apply and Close when you set up your wine.

Edit: One last thing, as Martje_001 said above, if you have linked your drives to your root partition, there's a big chance some .exe files saved somewhere, like your home directory, to have been infected. I don't have a recommendation for this... except for a good antivirus tool such as: 
[http://www.sophos.com/support/disinfection/klezh.html](http://www.sophos.com/support/disinfection/klezh.html) - Explains how to use sav32sfx.exe / SAV32CLI (I think you can use it through wine, never tried it)

---

### Post by lzsaver on 2008-07-27
> **xnostradamusx said:**
> i read some that dont use wine as a root user but i have no idea if i am opening some windows applications and there might be a spyware or virus
bundled with it.

Hi. Drive "z:" - ro-mode for users, and rw for root, afair.
Win-virus can infect only EXE-applications (but not ELF).
Scan ur files with this antivirus (in wine):
'ftp://ftp.drweb.com/pub/drweb/cureit/launch.exe'.
Or install this antivirus daemon+scanner: 
'ftp://ftp.drweb.com/pub/drweb/unix/Linux/ubuntu-7.04/'.

---

### Post by xnostradamusx on 2008-07-27
i checked my wine i think it created a fake C: Folder where all my installed windows application goes and i see all this windows files and stuff that you usually see in when you install something in your computer, just want to say i installed a program but automatically i got a internet explorer folder and an internet explorer.exe in the C: folder which is not connected with the program at all, i think its plan was to replace my internet.exe when your using a windows os and be infected without you noticing

and thanks for all the tips that had already posted ill try to use them all better to be sure than sorry

---

### Post by xnostradamusx on 2008-07-28
just an update i installed avast and did a thorough and entire system scanned.

so far 0 detected viruses, but everybody knows virus makers try to make them not be detectable by virus scanners so atlist im just 90 percent sure im already secured cause my firestarter always says im being attacked by an ip adress

---

