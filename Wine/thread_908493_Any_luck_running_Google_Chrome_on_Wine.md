---
title: "Any luck running Google Chrome on Wine?"
date: 2008-09-02
forum: Wine
---

### Post by Starks on 2008-09-02
It's out.

[http://www.google.com/chrome/eula.html](http://www.google.com/chrome/eula.html)

Different executable: [http://dl.google.com/update2/installers/ChromeSetup.exe](http://dl.google.com/update2/installers/ChromeSetup.exe)

---

### Post by jfernyhough on 2008-09-02
The web installer crashes when trying to connect to the net. I haven't managed to catch the downloaded installer in Windows yet, I'm going to have to play with folder permissions so it can't delete the downloaded file.

Looks good. Lightning quick. Doesn't mouse-scroll properly up and left though down and right work fine. Can't wait for the code to be rolled into Firefox 4.

---

### Post by jfernyhough on 2008-09-02
Success! This is the file that is downloaded and uncompressed (somewhere) on the system.

The original file is a 22MB 7zip, I recompressed it and it went down to 6MB. Just need to upload it somewhere...

---

### Post by jfernyhough on 2008-09-02
OK. Have at it. Rebooting myself now. :)

[http://www.mediafire.com/?sharekey=b79a12355acce174d2db6fb9a8902bda](http://www.mediafire.com/?sharekey=b79a12355acce174d2db6fb9a8902bda)

---

### Post by lolcese on 2008-09-02
Thanks, but it doesn't work for me.
After wine ./chrome.exe I get

fixme:ntdll:NtSetInformationProcess (0xffffffff,0x00000022,0x32fbd0,0x00000004) stub

---

### Post by Mercury_Alpha on 2008-09-02
Yeah, I get no dice either. WINE 1.1.3, right-click on "chrome.exe," select the WINE loader option -- and nothing happens. Ah well.

---

### Post by Tronex on 2008-09-02
Same problem here. I tried ChromeSetup.exe first, but got some problem with the IsAdminUser method...

---

### Post by jfernyhough on 2008-09-02
> **lolcese said:**
> Thanks, but it doesn't work for me.
After wine ./chrome.exe I get

fixme:ntdll:NtSetInformationProcess (0xffffffff,0x00000022,0x32fbd0,0x00000004) stubBah, same with me (Wine 1.1.3~winehq0~ubuntu~8.04-0ubuntu1).

---

### Post by nuttycc on 2008-09-02
fixme:ntdll:NtSetInformationProcess (0xffffffff,0x00000022,0x32fbd0,0x00000004) stub

I get this too. You're not allowed to use a native ntdll.dll (although I think I'm barking up the wrong tree by considering this).

"NtSetInformationProcess" comes up with quite a lot in google, none of which I understand, but someone else might :)

---

### Post by pili on 2008-09-02
haha
10 points to the first freak that get this working. Please post it on winedb

---

### Post by Uncle Che on 2008-09-02
Same error here

---

### Post by DutchDude on 2008-09-02
Same here. 

These are all my error messages if I try to run it in Terminal:

```
dude@dude-desktop1:~$ wine media/DATA/ChromeSetup.exe
wine: creating configuration directory '/home/dude/.wine'...
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
wine: '/home/dude/.wine' created successfully.
wine: cannot find 'media/DATA/ChromeSetup.exe'
dude@dude-desktop1:~$ wine /home/dude/.wine
wine: could not load L"Z:\\home\\dude\\.wine": Invalid handle

```

---

### Post by arkygeek on 2008-09-02
[http://dev.chromium.org/developers/how-tos/build-instructions-linux](http://dev.chromium.org/developers/how-tos/build-instructions-linux)

:-)

---

### Post by Gonzo_Dark on 2008-09-02
> **arkygeek said:**
> [http://dev.chromium.org/developers/how-tos/build-instructions-linux](http://dev.chromium.org/developers/how-tos/build-instructions-linux)

:-)


IF you read the page it says: **Note: If you want to use a Chromium-based browser, you should look elsewhere. Although many Chromium modules build under Linux and a few unit tests pass, nothing actually runs.**

So.. nothing actually runs. (sorry =/)

// GonzoDark

---

### Post by arkygeek on 2008-09-02
> **Gonzo_Dark said:**
> IF you read the page it says: **Note: If you want to use a Chromium-based browser, you should look elsewhere. Although many Chromium modules build under Linux and a few unit tests pass, nothing actually runs.**

So.. nothing actually runs. (sorry =/)

// GonzoDark

I did in fact read the page.  I am just happy that they are actively trying to make the native version work, and rather than  trying to make it work under wine I am going to try and contribute to making the linux version work...  :-)

---

### Post by solitaire on 2008-09-02
You have to install it in Windows first to get the real install files!

The install is 22Mb in size and consists of 2 files "Setup.exe" and "chrome.7z"

Can't get them to run in wine :(

---

### Post by Starks on 2008-09-02
BINGO!

[http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe](http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe)

Installs and runs (albeit buggy).

---

### Post by solitaire on 2008-09-02
this is what i get when i run the "Setup.exe" under wine
```

sol@Callisto:~$ wine ChromeSetup.exe
wine: could not load L"C:\\windows\\system32\\ChromeSetup.exe": Module not found

```
So I move the exe into the "System32" folder and run it again..
```

sol@Callisto:~$ wine ChromeSetup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12d1d0 0x33f930) stub!
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:winhttp:WinHttpOpen ((null), 1, (null), (null), 0x0): stub


```

---

### Post by Gonzo_Dark on 2008-09-02
> **Starks said:**
> BINGO!

[http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe](http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe)

Installs and runs (albeit buggy).

Did you get something up and running? and how if you did?

// GonzoDark

---

### Post by Starks on 2008-09-02
> **Gonzo_Dark said:**
> Did you get something up and running? and how if you did?

// GonzoDark
A simple "wine chrome_install.exe" on 1.1.3

---

### Post by solitaire on 2008-09-02
Not working for me :(
```

sol@Callisto:~$ wine ./chrome_installer.exe
err:setupapi:detect_compression_type cannot open file L"Z:\\-r"
err:setupapi:get_file_size cannot open file L"Z:\\-r"
expand.exe: can't open input file Z:\-r

```

---

### Post by Starks on 2008-09-02
> **solitaire said:**
> Not working for me :(
```

sol@Callisto:~$ wine ./chrome_installer.exe
err:setupapi:detect_compression_type cannot open file L"Z:\\-r"
err:setupapi:get_file_size cannot open file L"Z:\\-r"
expand.exe: can't open input file Z:\-r

```
Then remove the ./

---

### Post by solitaire on 2008-09-02
did that first!

Same error!!

---

### Post by ironcamel on 2008-09-02
I am having the same problem as Solitaire.  I tried without the ./ as well

---

### Post by solitaire on 2008-09-02
> **Starks said:**
> Then remove the ./


Hows your WINE setup??
Check the "Drives" folder and permissions..

---

### Post by Steveway on 2008-09-02
You can get the actual build from here: [http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/](http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/)
That get's you around using the installer since it is just a zip with everything in it.
But it still fails in wine.

---

### Post by Starks on 2008-09-02
> **solitaire said:**
> Hows your WINE setup??
Check the "Drives" folder and permissions..

I'm running the installer from my home directory. Wine interprets it as my Y: drive.

The only winetrick installed is msxml3.

---

### Post by Gonzo_Dark on 2008-09-02
download this: [http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe](http://cache.googlevideo.com/chrome/install/149.27/chrome_installer.exe)

and remember to use the new wine

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

it is not the final solution.. but it will get it running (well it crashes  after startup - but it is a good step in the right direction)

// GonzoDark

---

### Post by Steveway on 2008-09-02
You can get the actual build from here: [http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/](http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/)
That get's you around using the installer since it is just a zip with everything in it.
But it still fails in wine.
Oh, it doubleposted, strange...

---

### Post by ceeray on 2008-09-02
installer worked fine when I clicked it
the browser on the other hand is having problems opening google

---

### Post by Gonzo_Dark on 2008-09-02
[http://img218.imageshack.us/img218/6073/nicekq5.png](http://img218.imageshack.us/img218/6073/nicekq5.png)

with the guide I posted.

// GonzoDark

---

### Post by solitaire on 2008-09-02
OK latest WINE installed
Ran the installer..
It installs but just!!
Can't see any webpage just a black window. and the text is too big for most of the buttons!
Nearly there! :D lol

---

### Post by DutchDude on 2008-09-02
Mmmmm, apparently some people have more luck than others. I followed Gonzo_Dark's recipe, but I keep receiving error messages.

---

### Post by x82hammer28x on 2008-09-02
Same issue... this apparently only works with latest wine. Regular installer seems to run fine, get lots of errors out of Chrome though.

---

### Post by alexfarran on 2008-09-02
Installed using latest wine.  Runs, but can't render any web pages and the url bar is blacked out.

---

### Post by merlwiz79 on 2008-09-02
I have it installed but won't open any pages.
I have wine-doors 0.1.3 installed.
Using wine-doors I have installed windows installer 2, msxml4, common controls 5, and directx9.
Maybe one of these allows me to launch Google Chrome.
[[IMG]http://farm4.static.flickr.com/3188/2823150290_f6a0e7ee65.jpg[/IMG]]("http://farm4.static.flickr.com/3188/2823150290_048e2b366a_o.png")
Firefox in wine works, must be something specific to Google Chrome. :(

---

### Post by DutchDude on 2008-09-02
I reinstalled wine. Now I'm facing the same problem as the rest: runs, but can't render any web pages and the url bar is blacked out.

---

### Post by merlwiz79 on 2008-09-02
> **DutchDude said:**
> I reinstalled wine. Now I'm facing the same problem as the rest: runs, but can't render any web pages and the url bar is blacked out.

I can type in my url bar.
[[IMG]http://farm4.static.flickr.com/3207/2823201114_4858978390.jpg[/IMG]]("http://farm4.static.flickr.com/3207/2823201114_2ed00cc2b0_o.png")

---

### Post by DutchDude on 2008-09-02
> **merlwiz79 said:**
> I can type in my url bar.

me too, but the address bar is black. If I type [http://www.google.com](http://www.google.com)  and press enter, I see a "sad tab" (a small icon) with the text "Aw, Snap! Something went wrong whie displaying this web page. To continue, press Reload or go to another page."

(FYI, other pages and reloads do not work).

---

### Post by kendon on 2008-09-02
i had installed wine from hardy repos, if that matters. removed it, deleted ~/.wine and installed the latest wine. after installing the chrome_installer.exe i got an error msg, see attached screenshot.

wine gave me "Could not load Mozilla. HTML rendering will be disabled." when starting the installer, what should i install exactly?

//edit: damn, you were quicker. and you explained it correctly, the err msg appears when you try to open an url, not after the installation. same here, black url bar but can type.

---

### Post by merlwiz79 on 2008-09-02
[http://digg.com/tech_news/BREAKING_Google_Chrome_Just_Launched?t=18383763#c18387480]("http://digg.com/tech_news/BREAKING_Google_Chrome_Just_Launched?t=18383763#c18387480")
[QUOTE=Tiak]Apparently someone needs to impliment winhttp.dll's."WinHttpOpen"[/QUOTE].

---

### Post by donnykurnia on 2008-09-03
[http://bugs.winehq.org/show_bug.cgi?id=15106](http://bugs.winehq.org/show_bug.cgi?id=15106)

---

### Post by Rollerbob on 2008-09-03
I got a bit further by using winetricks.

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks riched20 riched30

I now get a working location bar, but still no web.

---

### Post by Tobu on 2008-09-03
I am able to browse most pages, though no https.

This is a recap of the [wine appdb page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635").

Grab wine 1.1.3 from the apt repository, instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) .

Grab the offline installer, eg at [http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe](http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe)

Grab winetricks, instructions at [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
 .

Run
```
winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins 

```

It runs very slow though, apparently the processes aren't lightweight at all.

---

### Post by ogcub on 2008-09-03
Wine AppDB shows it working with some tweaks, though i'm not able to reproduce 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30852](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30852)

---

### Post by Gonzo_Dark on 2008-09-03
[SIZE="5"]Here is a guide for the new browser Google Chrome[/SIZE]

*[SIZE="4"]Open your terminal and then follow the steps below[/SIZE]*

[SIZE="4"]First get WINE (the newest version)[/SIZE]

```



wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update


```

[SIZE="4"]Then install Chrome via the offline installer[/SIZE]

Download the file from the link below, then place the file on your desktop and double click on it.

```


http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe


```

[SIZE="4"]Then install riched20 and riched30  [/SIZE]

```


wget http://www.kegel.com/wine/winetricks
sh ./winetricks riched20 riched30


```

[SIZE="4"]and finally to get it all to work, do this[/SIZE]

```


winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins


```

[SIZE="4"]To use the program in the future(from the terminal), you need to run:[/SIZE]


```
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins 
```

[SIZE="4"] If you want to make a program icon in your tray, then do this:[/SIZE]

1. Right click on your menu and click and chose the option "Add to panel" and then "User defined program shortcut"

2. Now you can see a new window with the title "Make Shortcut" with the options "Name", "Command" and "Comment"

Under name you should write "Google Chrome", under "Command" you should use this code

```

env WINEPREFIX="/home/YOURUSERNAME/.wine" wine "C:\windows\profiles\YOURUSERNAME\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins 
```

remember to replace YOURUSERNAME with your user name ;) (both of them)

and then you should use this tray icon (click on the bouncing platform to change icon) 

```


/home/YOURUSERNAME/.local/share/icons/25e1_chrome.0.xpm


```

and again, remember to change "YOURUSERNAME" into your user name.

Hope it works for you ;)

Enjoy

// GonzoDark

ps. This is how it looks: [http://img231.imageshack.us/img231/6263/thereyouaregf1.png](http://img231.imageshack.us/img231/6263/thereyouaregf1.png)

pps. I am using the Danish version of Ubuntu and Chrome, so if I made any translation errors, then please correct me.

---

### Post by quazi on 2008-09-03
I can't quite get it to work.  I get as far as this line ```
sh ./winetricks riched20 riched30
```
but I can't run the second winetricks command (under user I get permission denied and sudo spits out command not found).

Then when I run the browser using that wine command it cannot load pages and crashes immediately.  Presumably my problem's coming in with the line ```

winetricks riched20 riched30
```

---

### Post by Gonzo_Dark on 2008-09-03
> **quazi said:**
> I can't quite get it to work.  I get as far as this line ```
sh ./winetricks riched20 riched30
```
but I can't run the second winetricks command (under user I get permission denied and sudo spits out command not found).

Then when I run the browser using that wine command it cannot load pages and crashes immediately.  Presumably my problem's coming in with the line ```

winetricks riched20 riched30
```

remember to do these steps, in the right order:

first

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

and then 

sh ./winetricks riched20 riched30

enjoy

---

### Post by Tjcrazy on 2008-09-03
I tried Gonzo_Duck's instructions. I tried running installer under wine and got:

> fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub


I got the latest version of wine (1.1.3)

Any help?

---

### Post by eragon100 on 2008-09-03
WWHEEE-AHH! It works, thanx for the guide. The attachment is a screenshot!

---

### Post by bradcater on 2008-09-03
> **Gonzo_Dark said:**
> [SIZE="5"]Here is a guide for the new browser Google Chrome[/SIZE]

*[SIZE="4"]Open your terminal and then follow the steps below[/SIZE]*

[SIZE="4"]First get WINE (the newest version)[/SIZE]

```



wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update


```

[SIZE="4"]Then install Chrome via the offline installer[/SIZE]

Download the file from the link below, then place the file on your desktop and double click on it.

```


[http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe](http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe)


```

[SIZE="4"]Then install riched20 and riched30  [/SIZE]

```


wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks riched20 riched30


```

[SIZE="4"]and finally to get it all to work, do this[/SIZE]

```


winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins


```

To use the program in the future, you need to run:


```
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins 
```


Enjoy

// GonzoDark

ps. This is how it looks: [http://img231.imageshack.us/img231/6263/thereyouaregf1.png](http://img231.imageshack.us/img231/6263/thereyouaregf1.png)

This works for me on Hardy 8.04 with the new Wine. Many thanks!

No https and very slow, but functional and pretty.

---

### Post by kendon on 2008-09-03
sweet, Gonzo_Darks howto works just fine, writing this in chrome on hardy, thx a lot.
it is actually slower than it is in my virtualboxed windows xp, so i still can't wait for the official linux version... ;)

---

### Post by kabotage on 2008-09-03
same thing for me, i cant browse any site. just want to share this.

flaws already discovered on google chrome that could exposed windows users to malicious hacker attacks ([http://blogs.zdnet.com/security/?p=1843](http://blogs.zdnet.com/security/?p=1843))

---

### Post by sdowney717 on 2008-09-03
It is working for me even though it does not like this command


Code:

winetricks riched20 riched30

scott@scott-desktop:~$ winetricks riched20 riched30
bash: winetricks: command not found

---

### Post by quazi on 2008-09-03
I actually followed the instructions exactly, ```
wget http://www.kegel.com/wine/winetricks
sh ./winetricks riched20 riched30
```
worked perfectly.

However I get ```

$ winetricks riched20 riched30
bash: Permission denied
$ sudo winetricks riched20 riched30
sudo: winetricks: command not found
```

and while running ```
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins
``` successfully opens chrome, it fails to render pages and closes immediately when I try to drag it.

I may just wait until it comes out for linux regardless as firefox is pretty damn good.

---

### Post by Cope57 on 2008-09-03
**[Watch what you post with chrome]("http://www.theregister.co.uk/2008/09/03/google_chrome_eula_sucks/")** <---- [SIZE="5"]Link[/SIZE]

> 11. Content licence from you

11.1 You retain copyright and any other rights that you already hold in Content that you submit, post or display on or through the Services. By submitting, posting or displaying the content, you give Google a perpetual, irrevocable, worldwide, royalty-free and non-exclusive licence to reproduce, adapt, modify, translate, publish, publicly perform, publicly display and distribute any Content that you submit, post or display on or through the Services. This licence is for the sole purpose of enabling Google to display, distribute and promote the Services and may be revoked for certain Services as defined in the Additional Terms of those Services. 

Just making you aware of the license which most people click through...

---

### Post by merlwiz79 on 2008-09-03
> **Cope57 said:**
> **[Watch what you post with chrome]("http://www.theregister.co.uk/2008/09/03/google_chrome_eula_sucks/")** <---- [SIZE="5"]Link[/SIZE]



Just making you aware of the license which most people click through...

Apparently it was a mistake and they have removed it from the new EULA.
[http://arstechnica.com/news.ars/post/20080903-google-on-chrome-eula-controversy-our-bad-well-change-it.html](http://arstechnica.com/news.ars/post/20080903-google-on-chrome-eula-controversy-our-bad-well-change-it.html)

---

### Post by dwasifar on 2008-09-03
I loaded Chrome in an XP vm, and it's pretty nice, but what concerns me about it is the lack of information from Google.  We didn't know about it until it was upon us.  When are Linux and Mac ports due?  Google isn't saying.  Even Apple is more forthcoming about future releases than this.  Given that this is an open source project, a little more transparency would be nice.

---

### Post by fbcsupport on 2008-09-03
Has anyone gotten a launcher to work for this yet? Using

env WINEPREFIX="/home/user/.wine" wine "C:\windows\profiles\user\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins

Does NOT work correctly from the launcher, but DOES work from a terminal window.

Any ideas?

---

### Post by XopherH on 2008-09-03
> **quazi said:**
> I actually followed the instructions exactly, ```
wget http://www.kegel.com/wine/winetricks
sh ./winetricks riched20 riched30
```
worked perfectly.

However I get ```

$ winetricks riched20 riched30
bash: Permission denied
$ sudo winetricks riched20 riched30
sudo: winetricks: command not found
```

and while running ```
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins
``` successfully opens chrome, it fails to render pages and closes immediately when I try to drag it.

I may just wait until it comes out for linux regardless as firefox is pretty damn good.


I do not get the permission denied error and message, but I do get command not found duo, although it says the following with bash instead of sudo as the shell.  I have to assume you have to be running as your home directory user, not sudo to get the correct permissions, as that is the only difference but that makes no sense.

```
winetricks riched20 riched30
bash: winetricks: command not found
```


I was able to open up a forum I visit regularly and it worked, so are your home directory permissions setup in a non-default way that would cut off Wine or anything else in all this?

---

### Post by merlwiz79 on 2008-09-04
You need to make sure you use this command or it won't work.
```
sh ./winetricks riched20 riched30
```
Just copy and paste the command and it will work.

---

### Post by Gonzo_Dark on 2008-09-04
> **fbcsupport said:**
> Has anyone gotten a launcher to work for this yet? Using

env WINEPREFIX="/home/user/.wine" wine "C:\windows\profiles\user\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins

Does NOT work correctly from the launcher, but DOES work from a terminal window.

Any ideas?

```

env WINEPREFIX="/home/YOURUSERNAME/.wine" wine "C:\windows\profiles\YOURUSERNAME\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins 
```

replace YOURUSERNAME with your user name ;) (both of them)

enjoy

// GonzoDark

---

### Post by jwilker2 on 2008-09-04
First thank you for the How-To!

However, It did not work for me...

After repeated attempts it appears that the step "Download the file from the link below, then place the file on your desktop and double click on it." fails to unpack and spread the 'chrome.exe' file into the appropriate subdirectory under 'local settings [...]'.

Double clicking on the 'Google Installer' does not yield an error and an examination of the object properties says it's being opened by 'wine'.

Any Ideas?

Again thanks!

> **Gonzo_Dark said:**
> [SIZE="5"]Here is a guide for the new browser Google Chrome[/SIZE]

*[SIZE="4"]Open your terminal and then follow the steps below[/SIZE]*

[SIZE="4"]First get WINE (the newest version)[/SIZE]

```



wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update


```

[SIZE="4"]Then install Chrome via the offline installer[/SIZE]

Download the file from the link below, then place the file on your desktop and double click on it.

```


[http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe](http://gpdl.google.com/chrome/install/149.27/chrome_installer.exe)


```

[SIZE="4"]Then install riched20 and riched30  [/SIZE]

```


wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks riched20 riched30


```

[SIZE="4"]and finally to get it all to work, do this[/SIZE]

```


winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins


```

[SIZE="4"]To use the program in the future(from the terminal), you need to run:[/SIZE]


```
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins 
```

[SIZE="4"] If you want to make a program icon in your tray, then do this:[/SIZE]

1. Right click on your menu and click and chose the option "Add to panel" and then "User defined program shortcut"

2. Now you can see a new window with the title "Make Shortcut" with the options "Name", "Command" and "Comment"

Under name you should write "Google Chrome", under "Command" you should use this code

```

env WINEPREFIX="/home/YOURUSERNAME/.wine" wine "C:\windows\profiles\YOURUSERNAME\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins 
```

remember to replace YOURUSERNAME with your user name ;) (both of them)

and then you should use this tray icon (click on the bouncing platform to change icon) 

```


/home/YOURUSERNAME/.local/share/icons/25e1_chrome.0.xpm


```

and again, remember to change "YOURUSERNAME" into your user name.

Hope it works for you ;)

Enjoy

// GonzoDark

ps. This is how it looks: [http://img231.imageshack.us/img231/6263/thereyouaregf1.png](http://img231.imageshack.us/img231/6263/thereyouaregf1.png)

pps. I am using the Danish version of Ubuntu and Chrome, so if I made any translation errors, then please correct me.

---

### Post by rafaeliga on 2008-09-04
someone had any luck with https pages ?

---

### Post by haelen on 2008-09-04
I get this error:

```
$ wine chrome_installer.exe
err:module:import_dll Library NDIS.SYS (which is needed by L"C:\\windows\\system32\\drivers\\npf.sys") not found
err:winedevice:ServiceMain driver L"NPF" failed to load

```

---

### Post by vishzilla on 2008-09-04
got it to work with wine but too slow. not worth. the perpetual wait for the linux version

---

### Post by crispy_420 on 2008-09-04
[http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html](http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html)

---

### Post by bitwaba on 2008-09-04
@ jwilker2

I had the same issue on mine.  For me, I had to check the chrome_installer log file found in ~/.wine/drive_c/windows/temp/ and it informed me that chrome was only built to run on windowsXP or greater.

Solution?  Run winecfg and in the Applications tab, change the Windows Version to Windows XP (mine was previously Windows 2000).

---

### Post by glenngds2007 on 2008-09-04
Then install riched20 and riched30

Code:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks riched20 riched30

and finally to get it all to work, do this

Code:

winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins


Then install Chrome via the offline installer

Download the file from the link below, then place the file on your desktop and double click on it.

Code:

[http://gpdl.google.com/chrome/instal..._installer.exe](http://gpdl.google.com/chrome/instal..._installer.exe)


This appears to be the order needed to get Chrome to run on my system.

Follow all other instructions as given!!!!!

---

### Post by Gonzo_Dark on 2008-09-04
> **glenngds2007 said:**
> Then install riched20 and riched30

Code:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks riched20 riched30

and finally to get it all to work, do this

Code:

winetricks riched20 riched30
wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --new-http --in-process-plugins


Then install Chrome via the offline installer

Download the file from the link below, then place the file on your desktop and double click on it.

Code:

[http://gpdl.google.com/chrome/instal..._installer.exe](http://gpdl.google.com/chrome/instal..._installer.exe)


This appears to be the order needed to get Chrome to run on my system.

Follow all other instructions as given!!!!!

The link to the offline installer is broken, and I already posted a guide ;)

[http://ubuntuforums.org/showpost.php?p=5719331&postcount=45](http://ubuntuforums.org/showpost.php?p=5719331&postcount=45)

// GonzoDark

---

### Post by Gonzo_Dark on 2008-09-04
> **crispy_420 said:**
> [http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html](http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html)

Nice guide, I guess more user friendly that mine ;)

// GonzoDark

---

### Post by janmartin on 2008-09-04
Anyone found a way how to import stuff from Firefox instead of by default suggested Microsoft IE?

The hard way would be to install Windows Firefox, then somehow transfer the bookmarks, passwords history etc. from Linux Firefox, and then import.

Anyone have a detailed How-to?

Thanks,
Jan

---

### Post by imgkg on 2008-09-04
check this site if this might help i guess google chrome can run on wine [http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html](http://www.myscienceisbetter.info/2008/09/install-google-chrome-on-linux-using-wine.html)

---

### Post by XopherH on 2008-09-04
> **merlwiz79 said:**
> You need to make sure you use this command or it won't work.
```
sh ./winetricks riched20 riched30
```
Just copy and paste the command and it will work.

```
**desktop:~$** sh ./winetricks riched20 riched30
Executing cabextract --directory=/home/chris/.wine/drive_c/winetrickstmp /home/chris/.winetrickscache/Q249973i.EXE
Extracting cabinet: /home/chris/.winetrickscache/Q249973i.EXE
  extracting /home/chris/.wine/drive_c/winetrickstmp/riched20.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/riched32.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/hotfix.exe
  extracting /home/chris/.wine/drive_c/winetrickstmp/hotfix.inf
  extracting /home/chris/.wine/drive_c/winetrickstmp/symbols/dll/riched20.dbg
  extracting /home/chris/.wine/drive_c/winetrickstmp/symbols/dll/riched32.dbg

All done, no errors.
Executing cp -f /home/chris/.wine/drive_c/winetrickstmp/riched20.dll /home/chris/.wine/drive_c/winetrickstmp/riched32.dll /home/chris/.wine/drive_c/windows/system32
Using native,builtin override for following DLLs: riched20 riched32
Executing wine regedit /home/chris/.wine/drive_c/winetrickstmp/override-dll.reg
Install of riched20 done
Executing cabextract --directory=/home/chris/.wine/drive_c/winetrickstmp /home/chris/.winetrickscache/InstMsiA.exe
Extracting cabinet: /home/chris/.winetrickscache/InstMsiA.exe
  extracting /home/chris/.wine/drive_c/winetrickstmp/msi.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/msiexec.exe
  extracting /home/chris/.wine/drive_c/winetrickstmp/msihnd.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/msisip.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/msimsg.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/msimain.sdb
  extracting /home/chris/.wine/drive_c/winetrickstmp/msiinst.exe
  extracting /home/chris/.wine/drive_c/winetrickstmp/riched20.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/usp10.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/msls31.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/shfolder.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/instmsi.msi
  extracting /home/chris/.wine/drive_c/winetrickstmp/imagehlp.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/cabinet.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/mspatcha.dll
  extracting /home/chris/.wine/drive_c/winetrickstmp/sdbapi.dll

All done, no errors.
Executing cp -f /home/chris/.wine/drive_c/winetrickstmp/riched20.dll /home/chris/.wine/drive_c/windows/system32
Using native,builtin override for following DLLs: riched20
Executing wine regedit /home/chris/.wine/drive_c/winetrickstmp/override-dll.reg
Install of riched30 done
winetricks done.
**desktop:~$** winetricks riched20 riched30
bash: /usr/sbin/winetricks: Permission denied
**desktop:~$** sudo winetricks riched20 riched30
sudo: winetricks: command not found
**desktop:~$** sudo ./winetricks riched20 riched30
sudo: ./winetricks: command not found

```

That is what I just ran, which is exactly what happened last night when I made the last post.

I noticed that on forums Chrome is really really really slow, but on simple pages its as fast as it should be through Wine.  It just feels like I'm using a 14.4 modem again.  I almost enjoy the nostalgia of it.

---

### Post by Ric_NYC on 2008-09-04
Thank you Gonzo_Dark!
It is working!
Websites like Youtube that have flash  make Chrome a little slow.



Google should hire you!:idea:



[http://img502.imageshack.us/my.php?image=snapshot1bo1.png](http://img502.imageshack.us/my.php?image=snapshot1bo1.png)

---

### Post by Gonzo_Dark on 2008-09-05
> **Ric_NYC said:**
> Thank you Gonzo_Dark!
It is working!
Websites like Youtube that have flash  make Chrome a little slow.



Google should hire you!:idea:



[http://img502.imageshack.us/my.php?image=snapshot1bo1.png](http://img502.imageshack.us/my.php?image=snapshot1bo1.png)

Hehe, they can send me a email if they want to :D

// GonzoDark

---

### Post by jtuchscherer on 2008-09-05
HI XoperH,
you need to make the winetricks file executable:

sudo chmod +x /usr/sbin/winetricks

That should do the trick. You don't need to use sudo to run winetricks

---

### Post by kendon on 2008-09-05
any hint how to make flash working? when i go on youtube they tell me i have to install the latest player. when trying to download flash from adobe chrome crashes.

quick test: when downloading a file (500mb) from my webserver on the same machine it crashes. downloading a torrent from tpb works fine. can anybody confirm that?

//edit: downloads are completed before chrome crashes. so a simple "wine install_flash_player.exe" did the trick. working fine now.

//edit2: actually _not_ fine. there are some horizontal glitches in the video. see screenshot.

---

### Post by DutchDude on 2008-09-06
Thanks for all the tips and suggestions above. 

After [installing Google Chrome on Ubuntu with Wine]("http://www.howtodude.net/howto/view.article.php/498"), I have been using it for a few days. For people who are to use it with high expectations, here is my evaluation:

- Google Chrome is becoming a great browser. It has some great innovations and I hope that it will inspire other browsers like Firefox.
- Google Chrome is not finished, not even in Windows. There are bugs, there are security problems. Anyway, it is a beta version.
- A browser for daily use should not run under Wine, it should run in Linux!
- Anyway, running Google Chrome on Ubuntu with Wine is a great way to satisfy your curiosity without the need to touch MS Windows. After all, we are on earth to play, to hack, to experiment.

---

### Post by YokoZar on 2008-09-06
> **DutchDude said:**
> - A browser for daily use should not run under Wine, it should run in Linux!
How is Wine not Linux?

---

### Post by misfitpierce on 2008-09-06
The font looks horrific in screenshot... I think i'll wait for linux/ubuntu release as to not waste resources and I dont really like running windows apps :P lol

---

### Post by carlxs99 on 2008-09-06
Quote:

This works for me on Hardy 8.04 with the new Wine. Many thanks!

No https and very slow, but functional and pretty.
---------------------------------------------------------------

I second that, https is not working.

Thank you very much for the guide and, therefore, the opportunity to test drive chrome before the linux release.

---

### Post by kendon on 2008-09-06
any improvements with wine 1.1.4? gonna try it now, changelog says something about chrome.

---

### Post by dwasifar on 2008-09-06
> **YokoZar said:**
> How is Wine not Linux?
You are a Ubuntu developer and you don't know the difference between running natively and running in an emulator?  ;)

---

### Post by Efros on 2008-09-06
Running using the instructions on tombuntu, chrome runs pretty well and very fast! FF takes an eon to start on my machine chrome is there almost immediately.

---

### Post by vishalrao on 2008-09-06
FF may be taking aeons to start due to extensions and even update checks for FF and its extensions which you can disable to speed up the startup a little...

---

### Post by martijnve on 2008-09-06
> **kendon said:**
> any improvements with wine 1.1.4? gonna try it now, changelog says something about chrome.

I have verified you no longer need a native version of winhttp.dll
I have also removed riched20 and riched32.dll installed with winetricks to get chrome working.

so it seems you now only need to run:
(sudo) apt-get install wine-dev (to get 1.1.4)
and then start chrome with "--new-http --in-process-plugins"

No more need to download extra dll's

---

### Post by Efros on 2008-09-06
doesn't work with https

---

### Post by mudgetheotter on 2008-09-06
If anyone is still having trouble with winetricks here's a list of directory's I had to chown with my username

~/.winetrickscache
~/.wine/drive_c/winetrickstmp

Hope this helps someone

---

### Post by zelrikriando on 2008-09-06
I managed to kinda install chrome. I cannot go on the internet with it...it's like chrome cannot connect on internet.

---

### Post by Efros on 2008-09-06
Follow the instructions at this [link]("http://tombuntu.com/index.php/2008/09/05/how-to-install-google-chrome-in-ubuntu-with-wine/")

---

### Post by vvvladut on 2008-09-06
I'm running wine 1.1.4. When I try to run chrome_installer.exe, I get this:

```
ankavlad@ankavlad-desktop:~/Desktop$ wine chrome_installer.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
ankavlad@ankavlad-desktop:~/Desktop$ fixme:shell:DllCanUnloadNow stub

```

I ran all steps in all tutorials I could find, including installing riched20 and riched30. Any ideas why it still doesn't work?

---

### Post by chocbar31 on 2008-09-06
Have you tried the Wine AppDB way yet? It finally worked for me....phew!!!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30832]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30832")

> First, get wine-1.1.4 (or build wine from git).

Then grab a fresh winetricks and .wine, and install the following packages (firefox only needed to download chrome):

cd $HOME
rm winetricks
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
mv .wine .wine.old
sh winetricks msxml3 corefonts firefox flash winxp

Using Firefox in Wine, download the online installer from chrome.google.com and let Firefox run it.

Or, if you already have Firefox installed, you can grab Chrome's installer like this:

wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe chrome.google.com

Don't let Chrome's installer start Chrome. Instead, to run Chrome, do:

wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --no-sandbox --new-http 
**

This part (sh winetricks msxml3 corefonts firefox flash winxp) would not work in one command for me, so I did them individually and they worked well that way.

---

### Post by BLTicklemonster on 2008-09-06
Had to get the latest version of Wine from their site in order to get the installer for chrome to work, but now the buggy little bugger works:

[[IMG]http://img211.imageshack.us/img211/8858/micksnutstq8.th.png[/IMG]](http://img211.imageshack.us/my.php?image=micksnutstq8.png)

Thanks for the how to.

---

### Post by aliask on 2008-09-07
> **dwasifar said:**
> You are a Ubuntu developer and you don't know the difference between running natively and running in an emulator?  ;)

Careful now - WINE actually stands for "WINE Is Not an Emulator".
It's a compatibility layer which translates the Windows API calls to native linux calls.

---

### Post by chocbar31 on 2008-09-07
Ha...chrome skins!

[http://www.freechromethemes.com/Download-Black-Google-Chrome-Theme.php]("http://www.freechromethemes.com/Download-Black-Google-Chrome-Theme.php")

Looks much better with a nicer skin :guitar:

Download a skin and unzip the default.dll file it contains

Replace the default.dll at the following location:

/home/USER/.wine/drive_c/windows/profiles/USER/Local Settings/Application Data/Google/Chrome/Application/0.2.149.29/Themes

Replace USER with your username!

---

### Post by vvvladut on 2008-09-08
> **chocbar31 said:**
> Have you tried the Wine AppDB way yet? It finally worked for me....phew!!!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30832]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635&iTestingId=30832")



This part (sh winetricks msxml3 corefonts firefox flash winxp) would not work in one command for me, so I did them individually and they worked well that way.

Thank you chocbar, will try this when I get home and will report.

I don't understand why I'd have to use FF under wine, but can't hurt to try it.

---

### Post by kendon on 2008-09-08
hm you're not gonna use it, just install it. i think it is an easy way to install some necessary parts in wine (correct me i i'm wrong).

---

### Post by chocbar31 on 2008-09-08
> **kendon said:**
> hm you're not gonna use it, just install it. i think it is an easy way to install some necessary parts in wine (correct me i i'm wrong).

Exactly...just a bridge, for the most part. You won't really even see it, it'll just download and install requirements.

---

### Post by YokoZar on 2008-09-09
> **dwasifar said:**
> You are a Ubuntu developer and you don't know the difference between running natively and running in an emulator?  ;)
How is Wine any different from any other Linux library to run applications, like GTK or SDL?

---

### Post by mrinvader on 2008-09-10
On Topic Response..

  Works Great with minor rendering glitches which may not be chrome related, but win32 flash related.. sometimes flash is upside down (celinedion.com) hehe..
  Everyone gripes about memory usage... I find 50mb incl the Wine components to be very competitive, especially considering the EARLY stage of beta.

Off Topic Response..

Wine is an API or an ABI. It is slightly more than just libraries like gtk. Better said, here is a rip from the wikipedia article about it..

Architecture

Wine implements the Windows API entirely in user-space, rather than as a kernel module at the time of writing. Services normally provided by the kernel in Windows are provided by a daemon known as wineserver. Wineserver implements basic Windows functionality, as well as providing extra functions such as X Window integration and translation of signals into native Windows exceptions.

---

### Post by knowmonger on 2008-09-10
I donno guys.Chrome doesn't seem to be "just another" browser. It has some serious memory management features which I think, will work only in a native run environment. Since its Open Source, I'm sure someone must have figured out a way to port it to Linux.

I'm looking for that kinda stuff. Anyway, this is great too. I tried it. I works. :)

---

### Post by hikaricore on 2008-09-12
I think I'll just sit this one out and wait for the Linux release. ^_^

---

### Post by dreamnid on 2008-09-13
> **Gonzo_Dark said:**
> ```

env WINEPREFIX="/home/YOURUSERNAME/.wine" wine "C:\windows\profiles\YOURUSERNAME\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins 
```

replace YOURUSERNAME with your user name ;) (both of them)

enjoy

// GonzoDark

I got the same problem where the launcher does not work (pages will not load), yet typing the exact same command in terminal works fine.

I tried both 
env WINEPREFIX="$HOME/.wine" wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application\chrome.exe" --new-http --in-process-plugins

and

env WINEPREFIX="/home/dreamnid/.wine" wine "c:\windows\profiles\dreamnid\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins

any ideas?

---

### Post by chocbar31 on 2008-09-17
> **dreamnid said:**
> I got the same problem where the launcher does not work (pages will not load), yet typing the exact same command in terminal works fine.

I tried both 
env WINEPREFIX="$HOME/.wine" wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application\chrome.exe" --new-http --in-process-plugins

and

env WINEPREFIX="/home/dreamnid/.wine" wine "c:\windows\profiles\dreamnid\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" --new-http --in-process-plugins

any ideas?

I tried different commands also, but the one that worked was:

*wine "$HOME/.wine/drive_c/windows/profiles/$USER/Local Settings/Application Data/Google/Chrome/Application/chrome.exe" --no-sandbox --new-http*

Eventhough Google Chrome works for me now, the above command successfully launches chrome. I even tried the commands you have posted and they don't work for me.

Just copy-n-paste!

---

### Post by munkiepus on 2008-09-20
There's now an easier way to run chrome on linux thanks to the folks at code weavers,

[http://www.codeweavers.com/services/ports/chromium/](http://www.codeweavers.com/services/ports/chromium/)


you can get the 32 bit ubuntu deb here:
[http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb](http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb)

or the 64 bit ubuntu deb here:
[http://media.codeweavers.com/pub/crossover/chromium/ia32-cxchromium_0.9.0-1_amd64.deb](http://media.codeweavers.com/pub/crossover/chromium/ia32-cxchromium_0.9.0-1_amd64.deb)

i've not tested them myself yet as i'm at work but i'll try it out when i get home and report back.

:)

---

### Post by MaverickCoast on 2008-09-20
Well, sort of. 

I have the 7.3 mb ChromeInstaller.exe file if someone has a place to put it for everyone to access. Seems that every link I clicked on was either a dead link or a link to the smaller kb file that won't work.

I DOWNLOADED THIS FILE VIA WINDOWS.

E-mail me or respond here with a location to upload the file to and I will get the file uploaded. I don't have a file sharing site that I use.

As far as I could find out, the best way to get Chrome installed, is to use a full .exe installation file and tweak your wine with this link: [http://ubuntuforums.org/showthread.php?t=908493&page=5](http://ubuntuforums.org/showthread.php?t=908493&page=5)

:guitar:

---

### Post by PaulusDev on 2008-09-23
Does anyone have trouble scrolling?
I have released a program for Windows which modifies chrome.dll to fix the issue (in Windows).
I just wanted to share it with you in case it can be of any use...I could even compile it for Ubuntu but since it fixes a Window only (at the moment) program, I am assuming there is no need.

Read more/download at:
[http://digg.com/software/Google_Chrome_68](http://digg.com/software/Google_Chrome_68)

---

### Post by Roaring Silence on 2008-09-24
> **mudgetheotter said:**
> If anyone is still having trouble with winetricks here's a list of directory's I had to chown with my username

~/.winetrickscache
~/.wine/drive_c/winetrickstmp

Hope this helps someone

Thanx. This helped me.
Roaring Silence

---

### Post by harry2006 on 2008-10-23
hi all, i installed chrome via wine couple of weeks ago. i must agree that its not at par with its windows counterpart. it takes really hell of time for a page to show up. but the its working atleast. so if you are really eager for chrome it seems we have to wait for some more time for a true deb/rpm/... release of Chrome. hope it'll be up to its expectations...till then happy firefoxing!!!

---

### Post by Tichondrius on 2008-10-23
That is exactly the reason I use Windows as the primary (host) OS, and run Linux as a guest in a virtual machine. That and gaming and better hardware support. 

P.S. firefox is a piece of trash, Chrome is awesome, it never crashes. But it badly needs mouse gestures

---

### Post by loneowais on 2008-10-24
Here is how to do it...

Very easy guide..
[URL="http://technology-included.blogspot.com/2008/10/google-chrome-on-ubuntu-linux.html"][COLOR="Red"]
http://technology-included.blogspot.com/2008/10/google-chrome-on-ubuntu-linux.html[/COLOR][/URL]:guitar:

---

### Post by loneowais on 2008-10-24
> **MaverickCoast said:**
> Well, sort of. 

I have the 7.3 mb ChromeInstaller.exe file if someone has a place to put it for everyone to access. Seems that every link I clicked on was either a dead link or a link to the smaller kb file that won't work.

I DOWNLOADED THIS FILE VIA WINDOWS.

E-mail me or respond here with a location to upload the file to and I will get the file uploaded. I don't have a file sharing site that I use.

As far as I could find out, the best way to get Chrome installed, is to use a full .exe installation file and tweak your wine with this link: [http://ubuntuforums.org/showthread.php?t=908493&page=5](http://ubuntuforums.org/showthread.php?t=908493&page=5)

:guitar:


You can use the 7mb install in the above mentioned method..

---

### Post by dmdil on 2009-11-19
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

this link have chrome for ubuntu 9.10

just save the file and install

---

### Post by shaceyMcbride10 on 2010-08-31
I have tried the steps you mention..But looks like something went wrong. Can't figure it out..:(

---

### Post by whitneyd on 2010-09-19
google chrome has its own standards for web building 
 
any luck running chrome on [http://gimmesomeluck.com](http://gimmesomeluck.com)

---

### Post by GeoPirate on 2010-09-21
I'm just curious, at this point why would somone try and run it on wine instead of using the linux version?

---

### Post by macem29 on 2010-09-21
also wondering, as chrome was based on chromium, why not just use chromium and skip the windows version, and wine? or is this the same question as the one above me?

---

### Post by Amathist on 2011-02-02
why not use the version for Ubuntu? it is in the repos. I use it  and it works fine.  they actually have two versions, chrome and chromium.  both are basicly the same really.

if you don't want to use the repos go here :
[http://www.google.com/chrome/eula.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha&installdataindex=homepagepromo](http://www.google.com/chrome/eula.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha&installdataindex=homepagepromo)

---

