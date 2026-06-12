---
title: "How to get Wine Windows Program Loader to open a program automatically?"
date: 2012-11-16
forum: Wine
---

### Post by GameGuru on 2012-11-16
Right now if I double left click a program it launches Archive Manager and gives me an error.  Only way I can run programs in the "Browse C:Drive" is by right clicking, choosing "Open With Wine Windows Program Loader."

Can I have this done automatically?  I would also love to make shortcuts on my desktop of these wine programs.  Can I?

I am using Ubuntu 12.10.  Thank you.

---

### Post by jerome1232 on 2012-11-16
Yes, you just have to change the default application to open the file. Just right click the file, click "Properties", Click the "Open With" tab, select "wine" and click "Set as Default".

---

### Post by GameGuru on 2012-11-16
Tried that, only Archive Manager is shown. If I click "Show other applications" it lists about 20 applications, none of them being Wine?

---

### Post by jerome1232 on 2012-11-16
Did you install wine through the repositories?

---

### Post by GameGuru on 2012-11-16
Yeah and they work when I right click and choose Wine.  When I type Wine this is what I get:

[IMG]http://i49.tinypic.com/2hrl7ck.png[/IMG]

Is this installed correctly?

---

### Post by jerome1232 on 2012-11-16
Looks like it, let's compare a few things between our systems, what does your mimeapps.list look like and do you have a wine.desktop file?

```
cat ~/.local/share/applications/mimeapps.list
```

```
ls /usr/share/applications | grep wine
```

---

### Post by djhk on 2012-12-09
Same problem here.
How does one add Wine to the list of application ?

---

### Post by Enkouyami on 2013-01-05
> **jerome1232 said:**
> Looks like it, let's compare a few things between our systems, what does your mimeapps.list look like and do you have a wine.desktop file?

```
cat ~/.local/share/applications/mimeapps.list
``````
ls /usr/share/applications | grep wine
```

Here's what I have:
```
cat ~/.local/share/applications/mimeapps.list
[Added Associations]
application/x-shellscript=gedit.desktop;
application/octet-stream=google-chrome.desktop;
x-scheme-handler/http=firefox.desktop;
x-scheme-handler/https=firefox.desktop;
x-scheme-handler/ftp=firefox.desktop;
x-scheme-handler/chrome=firefox.desktop;
text/html=firefox.desktop;
application/x-extension-htm=firefox.desktop;
application/x-extension-html=firefox.desktop;
application/x-extension-shtml=firefox.desktop;
application/xhtml+xml=firefox.desktop;
application/x-extension-xhtml=firefox.desktop;
application/x-extension-xht=firefox.desktop;
application/x-msdownload=gedit.desktop;

[Removed Associations]

[Default Applications]
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/ftp=firefox.desktop
x-scheme-handler/chrome=firefox.desktop
text/html=firefox.desktop
application/x-extension-htm=firefox.desktop
application/x-extension-html=firefox.desktop
application/x-extension-shtml=firefox.desktop
application/xhtml+xml=firefox.desktop
application/x-extension-xhtml=firefox.desktop
application/x-extension-xht=firefox.desktop
``````
ls /usr/share/applications | grep wine
q4wine.desktop
wine-browsedrive.desktop
wine.desktop
wine-notepad.desktop
wine-uninstaller.desktop
wine-winecfg.desktop
wine-winetricks.desktop
```

*Edit*
I fixed it by opening ~/.local/share/applications/mimeapps.list and setting wine.desktop as default for application/x-ms-dos-executable

---

### Post by jerome1232 on 2013-01-06
Glad it was that simple and that this thread at least helped someone :D

I assume you added a line like this under the [Added Associations] section and saved the file?

```
application/x-ms-dos-executable=wine.desktop;
```

Did you have to reboot or logout out/ log back in for the changes to take affect?

---

### Post by opethfan89 on 2013-02-26
I know this is an old thread, but this is exactly what I was looking for and helped me out alot.

I'm on Linux Mint 14 64-Bit (Cinnamon) and was able to add the line

```
application/x-ms-dos-executable=wine.desktop
```

to my ~/.local/share/applications/mimeapps.list file and Wine showed up as the default program.

I really hate how difficult it is to add a default program to the list otherwise.  There is no "browse to" option in the GUI interface, and that's pretty inconvenient for anyone coming from Windows, but that's a conversation for another thread.

Thanks for posting the solution, OP!!

---

### Post by RobertSwipe on 2013-04-15
This solution worked for me too - thanks.

---

### Post by mc33 on 2013-06-30
This thread works for Ubuntu 13.04. Thanks!

---

### Post by donmyers on 2013-10-02
Hi,

I did a clean install of Ubuntu 13.10 Beta 2 (final) yesterday. I installed wine from the repository (1.4.1). The install went fine but it would not give me the menu option of opening a .exe file to install windows programs. I thought there might be a dependency problem and uninstalled and reinstalled Wine. Still no luck. Then I uninstalled again, and downloaded 1.6 from the repository. Still no luck. Finally I found this thread. My mimeapps.list was empty, but I added the following:
  	 	 	 	   *[SIZE=2][Added Associations] [/SIZE]* 
 [I][SIZE=2]application/x-ms-dos-executable=wine.desktop
and it is working like a charm now. Thank you to everyone who posted above.
[/SIZE][/I]

---

### Post by romain-b on 2013-11-07
Hey !

Same problem with ubuntu 13.10, but the solution does not work for me : there is no ~/.local/share/applications/mimeapps.list !  (even if I check for masked files...)
(As a newbie I found that anoying... Will Wine install progress one day ? The topic is not new it seems... Hopefully there is a community !)
Thanks in advance for any help...

(PS : I'm trying to install microsoft office 2003, needed for my work, first using playonlinux but it doesn't work, now with Wine...)
:confused:

---

### Post by Baldrick_NZ on 2013-11-07
> **romain-b said:**
> I'm trying to install microsoft office 2003, needed for my work, first using playonlinux but it doesn't work, now with Wine...)
:confused:

Have you considered LibreOffice or Kingsoft ([http://www.noobslab.com/2013/05/microsoft-office-alternative-kingsoft.html](http://www.noobslab.com/2013/05/microsoft-office-alternative-kingsoft.html)) as native alternatives to Office? Kingsoft is designed as a drop in replacement for those coming directly from a Windows background. LibreOffice can edit/save .doc/.docx/.xls, etc... too.

Try them both, you might be pleasantly surprised. :-)

---

