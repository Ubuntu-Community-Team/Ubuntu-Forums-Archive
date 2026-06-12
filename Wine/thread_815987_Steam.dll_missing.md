---
title: "Steam.dll missing"
date: 2008-06-02
forum: Wine
---

### Post by ukblacknight on 2008-06-02
Hi, after installing Half Life 2, along with CS:S and so on, I am unable to play any of the games as I receive the message "Main Exception error, cannot load library steam.dll".

If I try to install steam, I get the same error message.

I installed Counter-Strike: Condition Zero, tried installing steam on that and it has the same error message when installing.  I did find steam.dll in the CZ folder, copied it to the HL2 area, and the game now produces the following message: Main exception error, cannot load library steamui.dll".

I'm unable to play Condition Zero too because I get a software emulation software detected error!

Does anyone know why I'm unable to install steam or play the games?

Ubuntu 8.10
Wine 0.9.60

---

### Post by cogadh on 2008-06-02
It might have something to do with the order you are doing things in. You need to follow some pretty specific steps to get Steam running:[LIST=1]
[*]Install wine and the winbind package, then configure wine/create the .wine directory:```
sudo apt-get install wine winbind
winecfg
```
[*]Install the Wine Gecko HTML engine. Run the following, then follow the prompts. You will know the Gecko engine is installed correctly when the WineHQ webpage is displayed: ```
wine iexplore http://www.winehq.org
```
[*]Install Flash Player for Windows. Download the Flash Player installer for Windows from the Adobe website, then run this:```
cd /to/wherever/you/put/the/installer
wine install_flash_player.exe
```
[*]Install and configure Steam. Download the Steam installer from the Steam website and install it:```
cd /to/wherever/you/put/the/installer
wine start SteamInstall.msi
```After it has been installed a couple of configuration changes need to be made:[list=a]
[*]Click on File > Settings to bring up Steam's settings menu.
[*]Click on the Interface tab and uncheck the "Run Steam when Windows starts" box
[*]Click on the In-game tab and uncheck the "Enable Steam Community In-game" box[/list]
[*]Install games just like you normally would within Steam.
[/LIST]
Now, to run the games, it is usually best to launch Steam first, then use Steam to launch the game. You can use the menu or desktop shortcuts that were created for Steam to do that, or if you run it from the terminal, do this:
```
cd ~/.wine/drive_c/Program\ Files/Steam
wine Steam.exe
```

---

### Post by ukblacknight on 2008-06-02
Thanks for the reply.  I've got no internet at the moment (I'm at work) so I can't do most of these until July.  I haven't done most of those steps, so that's probably why it's not working!  I have emailed myself (can read on my phone) two commands which enable the games to run without steam, so I'll try that tonight.

I'll post the result in July.

---

### Post by ReconUnit415 on 2008-06-19
Thankyou very very much for the help. I had the exact same problem and it worked out perfectly.
I have a question though. I am having real trouble with right-click or drop down menus. They appear somewhere completely off where they are supposed to be. I have to move my cursor around the screen until I see the menu light up because I selected it, then I have to use the arrow keys to highlight my choice and then hit enter. Any fixes? Please replay via PM so I am noticed, for I am rarely on this forum.

---

### Post by cogadh on 2008-06-19
I don't like to reply to threads in PM form, unless it is really required. I'm sure other people have the same question as you, and it would be better to answer all of them in this one place.

The cursor alignment issue is a known problem with Steam in Wine. It was supposedly corrected for Wine 1.0, but I have already seen a few reports of it still happening. If you haven't updated to 1.0 yet, try that to see if it fixes the issue. If you already have 1.0, then you will probably have to put up with the issue until the next stable Wine release (should be in a few months).

---

### Post by kubug on 2008-07-12
I have to say that the above did not work for me. I ran all what you said, but I still get the same message. I guess wine still doesn't like msi installers. 

It looks like the dlls simply do not get installed. I was looking for a manual way to get them, but so far no go.

---

### Post by -|Veni_Vidi_Vici*- on 2008-07-12
> **kubug said:**
> I have to say that the above did not work for me. I ran all what you said, but I still get the same message. I guess wine still doesn't like msi installers. 

It looks like the dlls simply do not get installed. I was looking for a manual way to get them, but so far no go.

I think he has step 4 wrong. I believe that was an older wine version.
```

Install and configure Steam. Download the Steam installer from the Steam website and install it:

cd /to/wherever/you/put/the/installer
wine start SteamInstall.msi
```

Here's what I did: 
```
cd /to/wherever/you/put/the/installer
wine msiexec /i SteamInstall.msi
```
As per [these instructions](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)(step 3.1). I'm not sure what "start" or "msiexec /i" do, but the latter worked for me (with wine 1.0x or whatever the latest is).

P.S.If you install it correctly the dlls should get unpacked, if not I would try to make sure that the files are there. If not, put them in the appropriate place in the steam directory. If they are there, wine just isn't aware of them. Wine has a file which lists all of the installed dlls. You have to edit this file and add the dll in there if it is not. Unfortunately I do not know what file it is, but I'm sure its easy to find out.

P.P.S I have the cursor problem too. Instead of the top corner pointing, it's the bottom corner. I suppose you could always get an upside-down cursor, but I've gotten used to it. Besides, when playing games on steam the cursor is aligned correctly, it's just the menus that are the problem.

---

### Post by I[AM]SMRT on 2008-10-20
I've been dealing with this problem all day.

If you're having problems with the SteamUI.dll, it means that something's interfering with Steam's internet connection. In my case it was moblocker. I unblocked Valve, got the update but for some reason I'm getting the error again, I wonder what it is ._.

[https://support.steampowered.com/kb_article.php?ref=2198-AGHC-7226](https://support.steampowered.com/kb_article.php?ref=2198-AGHC-7226)

EDIT: It's not my router =/.

EDIT: Ah, it's because I added steamui.dll to the winecfg libraries.

---

