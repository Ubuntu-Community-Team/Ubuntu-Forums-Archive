---
title: "Steam: Firefox Protocol Handler How-To"
date: 2007-05-05
forum: Wine
---

### Post by fatbuttlarry on 2007-05-05
**[COLOR="Red"]*Note:  This how-to requires wine, steam, and firefox.[/COLOR]**

[[img]http://ubuntuforums.org/attachment.php?attachmentid=31800&stc=1&d=1178355502[/img]](http://www.winehq.org/site/download) [SIZE="6"]+[/SIZE] [[img]http://ubuntuforums.org/attachment.php?attachmentid=31801&stc=1&d=1178355750[/img]](http://www.steampowered.com)[SIZE="6"]+FIREFOX[/SIZE] 


Ever want those cool links like:```
steam:"-applaunch 70 +connect  vnny.dyndns.org:27015"
```
to work with Steam under Ubuntu?

It can be done.  This is how I did it.

[LIST]
[*]First, create the following script: **/usr/bin/steam**
(Type this in a console window)```
sudo pico /usr/bin/steam
```
(Type this text)```
#!/bin/sh
#
# Steam wrapper script
#
exec wine "c:\\program files\\steam\\steam.exe" "$@"

```

(Alternately, you can download it here: [img]http://ubuntuforums.org/images/uf/attach/gz.gif[/img] [steam.tar.gz](http://ubuntuforums.org/attachment.php?attachmentid=31797&d=1178354817) (203 Bytes)
[*]Ensure the new file is executable:
```
sudo chmod +x /usr/bin/steam
```
[/LIST]

[COLOR="Red"]Firefox 3.5 and higher:[/COLOR]
[LIST=1]
[*]Navigate your firefox browser to **about:config**
[*]Set up the following values in firefox's **about:config** page
**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.expose.steam
```
(Boolean Value)```
false
```
[*]Click a Steam hyperlink: [[sample link](steam://open/friends)]
[*]When prompted for the application, Click "Browse" and paste the path to our executable:
```
/usr/bin/steam
```
[*]Click the check box to remember this application for Steam links
[*][You are finished.](http://ubuntuforums.org/attachment.php?attachmentid=31798&d=1178354998)
[/LIST]


[COLOR="Red"]Firefox 3.0 and older:[/COLOR]
[LIST=1]
[*]Navigate your firefox browser to **about:config**
[*]Set up the following values in firefox's [**about:config**](http://ubuntuforums.org/attachment.php?attachmentid=31796&stc=1&d=1178355091) page
**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.external.steam
```
(Boolean Value)```
true
```
**Right Click >> New >> String:**
(Preference Name)```
network.protocol-handler.app.steam
```
(String Value)```
steam
```

**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.warn-external.steam
```
(Boolean Value)```
false
```
[*]Test to see if it works: [[sample link](steam://open/friends)] and [enjoy](http://ubuntuforums.org/attachment.php?attachmentid=31798&d=1178354998)!
[*]You are finished.
[/LIST]


-Tres

---

### Post by Darko-TheRaven on 2007-05-07
I just spotted a mistake.

network.protocol-handler.external.steam

is in the image but you do not specify to add that preference

---

### Post by fatbuttlarry on 2007-05-07
Thanks!  Fixed! Cheers.

-Tres

---

### Post by KillerKiwi on 2007-05-08
Im pretty sure you could do this in gconf... then the links would work in all gnome apps

---

### Post by fatbuttlarry on 2007-05-08
> **KillerKiwi said:**
> Im pretty sure you could do this in gconf... then the links would work in all gnome apps
Good idea.

Does it matter if I don't run gnome lol?

I'll apt-get that and see what it does! :)

-Tres

---

### Post by fatbuttlarry on 2007-05-08
Currently running the following command to get gconf installed:
```

apt-get install gconf-editor

```

Then got CORBA errors.  So I created a key thing, and it didn't show up.

I re-opened the program and some stuff was listed.  Looks kind of like a registry.  Cool. Lol I'm stopping that project right there. :)

-Tres

:popcorn:

---

### Post by KillerKiwi on 2007-05-08
gconf is like a registry (windows like *ugg* ) only in the fact that its centralised... you can delete it corrupt it etc any everything will still work as the settings are actually distributed xml files.

Just to clarify it is NOT like the windows regiestry

END RANT

anyway you can create gconf keys like this (NOTE: you are ment to create an XML fall back but this hack works fine)

gconftool-2 -t string -s /desktop/gnome/url-handlers/steam/command exec wine "c:\\program files\\steam\\steam.exe" "%s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/steam/enabled true 
gconftool-2 -t bool -s /desktop/gnome/url-handlers/steam/needs_terminal false 

for KDE you can do this



[Protocol]
exec=wine "c:\\program files\\steam\\steam.exe" '%u'
protocol=steam
input=none
output=none
helper=true
listing=false
reading=false
writing=false
makedir=false
deleting=false
icon=package
Description=steam

Save this code in ${KDEHOME}/share/services/steam.protocol

---

### Post by fatbuttlarry on 2007-05-08
> **KillerKiwi said:**
> gconf is like a registry (windows like *ugg* ) only in the fact that its centralised... you can delete it corrupt it etc any everything will still work as the settings are actually distributed xml files.

Just to clarify it is NOT like the windows regiestry

END RANT

anyway you can create gconf keys like this (NOTE: you are ment to create an XML fall back but this hack works fine)

gconftool-2 -t string -s /desktop/gnome/url-handlers/steam/command exec wine "c:\\program files\\steam\\steam.exe" "%s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/steam/enabled true 
gconftool-2 -t bool -s /desktop/gnome/url-handlers/steam/needs_terminal false 

for KDE you can do this



[Protocol]
exec=wine "c:\\program files\\steam\\steam.exe" '%u'
protocol=steam
input=none
output=none
helper=true
listing=false
reading=false
writing=false
makedir=false
deleting=false
icon=package
Description=steam

Save this code in ${KDEHOME}/share/services/steam.protocol
It's my guess, that if I'm using KDE w/ Firefox, Firefox will only know the gconf settings, where as Konqueror will only know the KDE settings?

This is really cool stuff.  Perhaps it's a better solution around the Firefox hack that started this thread.  I guess I make a false assumption that most people using steam run firefox, which may not be the case. :guitar: 

If I can get these changes to take and work, I will update the how-to with the more abstract settings.

BTW - Does anyone know how to remove these settings from Firefox once they've been created?  Lol, I might want to take them back out for testing!

-Tres

---

### Post by Orffen on 2007-05-11
I also had to do a 

```
sudo chmod +x /usr/bin/steam
```

before Firefox would properly handle it. It gave error

> "Firefox doesn't know how to open this address, because the protocol (steam) isn't associated with any program."

The message is confusing, but [has been raised in the Mozilla Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=312953).

---

### Post by fatbuttlarry on 2007-05-11
Thanks Orffen!  Added to How-To!

-Tres

---

### Post by fatbuttlarry on 2007-05-14
I have decided not to update this with the gconf / kde keys for now.  I am working on another project at this time, so I'll leave it be until people have problems, etc. :popcorn:

---

### Post by Riboflavin on 2009-05-15
Thanks! This worked great for me with the latest version of wine and ubuntu :)

---

### Post by frodomir on 2009-05-17
Dude Im not Einstein  What the hell does this mean 


```
# Create the following script: /usr/bin/steam (Type this in a console window) Code:  sudo pico /usr/bin/steam  (Type this text) Code:  #!/bin/sh # # Steam wrapper script # exec wine "c:\\program files\\steam\\steam.exe" "$@"  (Alternately, you can download it here: steam.tar.gz (203 Bytes) # Ensure the new file is executable: Code:  sudo chmod +x /usr/bin/steam  # Test to see if it works: [sample link] and enjoy!
```

---

### Post by fatbuttlarry on 2009-05-17
Einstein,

If you need help, you're going to have to be more specific on what part of the how-to you don't understand.

-Tres

---

### Post by frodomir on 2009-05-17
> **fatbuttlarry said:**
> Einstein,

If you need help, you're going to have to be more specific on what part of the how-to you don't understand.

-Tres

Im not coding or whatsoever einstein and dont you see i said i dont understand from script creating and so on part... I do not know what usr/so on means what to do... Nothing...

Sorry for being like this, its just ive een trying to download it half of day... Both IE (6, 8) FF (2, 3), opera... None owrked

[IMG]http://i41.tinypic.com/15wdzmg.jpg[/IMG]


Idk what to do after this part

---

### Post by fatbuttlarry on 2009-05-17
Einstein,

What are you trying to "download?"

This tutorial is for a script that launches Steam (Half-Life) in Ubuntu.

Your screenshot confuses me a little as I see the Windows version of Firefox running.  The tutorial is for making a game launch from the Ubuntu version of Firefox.  Is that what you are trying to do?

Please explain.

-Tres

---

### Post by frodomir on 2009-05-18
> **fatbuttlarry said:**
> Einstein,

What are you trying to "download?"

This tutorial is for a script that launches Steam (Half-Life) in Ubuntu.

Your screenshot confuses me a little as I see the Windows version of Firefox running.  The tutorial is for making a game launch from the Ubuntu version of Firefox.  Is that what you are trying to do?

Please explain.

-Tres

IDK what you are talknig about :lolflag: Like I said IM kinda new to all this stuff...

I have WIN Vista, And firefox is my main browser...

Is there any way to make it work? I tried to edit reg keys like said on steam forums but Im having ownership problems, even I have only 1 account... I cant just take rights, idk why, so that trick fails for me...

---

### Post by fatbuttlarry on 2009-05-18
> **frodomir said:**
> IDK what you are talknig about :lolflag: Like I said IM kinda new to all this stuff...

I have WIN Vista, And firefox is my main browser...

Is there any way to make it work? I tried to edit reg keys like said on steam forums but Im having ownership problems, even I have only 1 account... I cant just take rights, idk why, so that trick fails for me...

Well that would explain why the thread reads foreign to you.  This is not a Windows forum (nor Vista for that matter).  

This forum is for Ubuntu Linux.  The tutorial you are reading is for Linux, not Windows, so many of the steps will not work.  If you are having difficulties with Steam in Vista I suggest first visiting: [http://store.steampowered.com/forums/](http://store.steampowered.com/forums/) and asking there.

Firefox on Windows should automatically process your steam links.  If you are having problems getting steam running, search a bit more on Google, there's quite a few instructions on it.

I can try to help you outside of this thread via IM if you'd like.  FatButtLarry on AIM, MSN, Yahoo or Google chat.

Good luck.

-Tres

---

### Post by frodomir on 2009-05-19
> **fatbuttlarry said:**
> Well that would explain why the thread reads foreign to you.  This is not a Windows forum (nor Vista for that matter).  

This forum is for Ubuntu Linux.  The tutorial you are reading is for Linux, not Windows, so many of the steps will not work.  If you are having difficulties with Steam in Vista I suggest first visiting: [http://store.steampowered.com/forums/](http://store.steampowered.com/forums/) and asking there.

Firefox on Windows should automatically process your steam links.  If you are having problems getting steam running, search a bit more on Google, there's quite a few instructions on it.

I can try to help you outside of this thread via IM if you'd like.  FatButtLarry on AIM, MSN, Yahoo or Google chat.

Good luck.

-Tres


awww... Pity... I browsed steam forums for error but nothing helped me with getting it clear...

---

### Post by harry71194 on 2009-11-30
I followed the instructions exactly, and yet I still get
> Firefox doesn't know how to open this address, because the protocol (steam) isn't associated with any program.

---

### Post by fatbuttlarry on 2009-12-01
Harry,

This tutorial was written a long time ago.  What version of Ubuntu are you running?  I can attempt to recreate the error.

-Tres

---

### Post by 8Kuula on 2009-12-02
steam://run/33190 ([http://store.steampowered.com/app/33190/](http://store.steampowered.com/app/33190/))

"Firefox doesn't know how to open this address, because the protocol (steam) isn't associated with any program."

Firefox config:
```
network.protocol-handler.app.steam;steam
network.protocol-handler.external.steam;true
network.protocol-handler.warn-external.steam;false
```

Firefox 3.5.5, Ubuntu 9.10 64bit

*scratching head*

---

### Post by fatbuttlarry on 2009-12-02
Ok, I've tried this with Firefox 3.5.5 on Kubuntu 9.10 32-bit and I get the same error.

It appears the [format has changed with Firefox 3.5]("http://kb.mozillazine.org/Register_protocol#Firefox_3.5_specific__.28works_without_installed_Gnome_libraries.29").  I will investigate further.

If anyone else figures it out, please post!

-Tres

---

### Post by 8Kuula on 2009-12-02
$ gconftool-2 -s /desktop/gnome/url-handlers/steam/command 'wine "D:\Steam\steam.exe" "%s"' --type String
$ gconftool-2 -s /desktop/gnome/url-handlers/steam/enabled --type Boolean true

Works?

[s]How I can delete those firefox configurations? :P right click menu do not have delete :D[/s]
nvm, edited prefs.js file in firefox profile, clered them out.

---

### Post by fatbuttlarry on 2009-12-02
Figured it out.  [Tutorial appended for Firefox 3.5+ users]("http://ubuntuforums.org/showthread.php?t=433548").  Feedback welcome.

---

### Post by 8Kuula on 2009-12-03
Seems to work :)

---

### Post by fatbuttlarry on 2009-12-03
Thanks for testing. :popcorn:

---

### Post by theBishop on 2010-03-30
This isn't working for me.  Ubuntu 9.10.  Firefox version 3.5.8

---

### Post by theBishop on 2010-04-03
Any help with this?  I am unable to download Steam demos on Ubuntu.

---

### Post by fettuohi on 2010-04-08
Works also in Firefox 3.6.3 on Arch Linux. Manty thanks for this guide :).

André

---

### Post by johnathanamber on 2010-07-07
Hey everyone!

I realize that this is for FF but, is there a way to make this work for Google Chrome?

I do have FF installed, but I don't normally use it.

Thank you and God bless,
Johnathan

---

### Post by fatbuttlarry on 2010-07-07
Johnathan,

Great question.  Here's a quote from a [Chrome bug report]("http://code.google.com/p/chromium/issues/detail?id=18113") that has some insight into it.  It's in reference to the Ubuntu "apt" protocol, but may apply to all protocols in the KDE and Gnome desktops.

Unfortunately I'm having a hard time getting the suggestions to work, so if you or someone else can offer some insight, I'd be happy to re-write a cross-browser version of this tutorial.

> Once [http://code.google.com/p/chromium/issues/detail?id=20731](http://code.google.com/p/chromium/issues/detail?id=20731) is taken care of, 
unknown protocol schemes like apt: will cause a warning dialog and then use xdg-open 
to invoke the desktop environment's handler for the URL. GNOME and KDE both come with 
broken support for apturl (at least on Ubuntu 8.04) but are easily fixed.

```
In GNOME, run:
gconftool-2 --set --type string /desktop/gnome/url-handlers/apt/command "apturl %s"

In KDE, create a file ~/.kde/share/services/apt.protocol containing this:
[Protocol]
exec=apturl "%u"
protocol=apt
input=none
output=none
helper=true
listing=false
reading=false
writing=false
makedir=false
deleting=false
URIMode=rawuri
```


I don't recommend anyone copies and pastes any of the above code verbatim.  This is here as a starting point.  Also important is that the "/home/... .../services" folder in KDE has moved to a KDE4 folder.  Still no luck on my end getting it working though in either location.

-Tres

---

### Post by BadboyXD on 2011-04-01
I prettymuch got stuck after the part where I put in the:
]#!/bin/sh
#
# Steam wrapper script
#
exec wine "c:\\program files\\steam\\steam.exe" "$@"

Cause now Im stuck with a bunch of text donno if Im supposed to save it somehow. Or if I am don't know how to save it. Just stuck with the terminal atm with no idea how to move forward. > **fatbuttlarry said:**
> **[COLOR=Red]*Note:  This how-to requires wine, steam, and firefox.[/COLOR]**

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31800&stc=1&d=1178355502[/IMG]]("http://www.winehq.org/site/download") [SIZE=6]+[/SIZE] [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31801&stc=1&d=1178355750[/IMG]]("http://www.steampowered.com")[SIZE=6]+FIREFOX[/SIZE] 


Ever want those cool links like:```
steam:"-applaunch 70 +connect  vnny.dyndns.org:27015"
```to work with Steam under Ubuntu?

It can be done.  This is how I did it.

[LIST]
[*]First, create the following script: **/usr/bin/steam**
(Type this in a console window)```
sudo pico /usr/bin/steam
```(Type this text)```
#!/bin/sh
#
# Steam wrapper script
#
exec wine "c:\\program files\\steam\\steam.exe" "$@"

```(Alternately, you can download it here: [IMG]http://ubuntuforums.org/images/uf/attach/gz.gif[/IMG] [steam.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=31797&d=1178354817") (203 Bytes)
[*]Ensure the new file is executable:
```
sudo chmod +x /usr/bin/steam
```
[/LIST]

[COLOR=Red]Firefox 3.5 and higher:[/COLOR]
[LIST=1]
[*]Navigate your firefox browser to **about:config**
[*]Set up the following values in firefox's **about:config** page
**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.expose.steam
```(Boolean Value)```
false
```
[*]Click a Steam hyperlink: [[sample link]("steam://open/friends")]
[*]When prompted for the application, Click "Browse" and paste the path to our executable:
```
/usr/bin/steam
```
[*]Click the check box to remember this application for Steam links
[*][You are finished.]("http://ubuntuforums.org/attachment.php?attachmentid=31798&d=1178354998")
[/LIST]


[COLOR=Red]Firefox 3.0 and older:[/COLOR]
[LIST=1]
[*]Navigate your firefox browser to **about:config**
[*]Set up the following values in firefox's [**about:config**]("http://ubuntuforums.org/attachment.php?attachmentid=31796&stc=1&d=1178355091") page
**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.external.steam
```(Boolean Value)```
true
```**Right Click >> New >> String:**
(Preference Name)```
network.protocol-handler.app.steam
```(String Value)```
steam
```**Right Click >> New >> Boolean:**
(Preference Name)```
network.protocol-handler.warn-external.steam
```(Boolean Value)```
false
```
[*]Test to see if it works: [[sample link]("steam://open/friends")] and [enjoy]("http://ubuntuforums.org/attachment.php?attachmentid=31798&d=1178354998")!
[*]You are finished.
[/LIST]


-Tres

---

