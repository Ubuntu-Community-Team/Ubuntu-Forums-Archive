---
title: "WinCVS line 736 error"
date: 2008-03-08
forum: Wine
---

### Post by oki-vino on 2008-03-08
Hey guys..I hope this is the correct forum. I am trying to install Cedega CVS style, but I get an error during the "2- Checkout stage". I get this:
------------------------------
--------- Error log - file /home/sean/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/sean/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
--------------------------------------------



I am running Ubuntu 7.10, and I used the install procedure over at [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&back=HOWTO+INDEX+Wine]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&back=HOWTO+INDEX+Wine")

The only problem I had with installing the packages was that "x-window-system-dev" wouldn't install.

i am a first itme linux user, and I just started up Ubuntu a couple days ago, so..ya know..use n00b language!

Thanks!

---

### Post by happyhamster on 2008-03-08
- Try installing xserver-xorg-dev (and build-essential just to be sure):

sudo apt-get install xserver-xorg-dev build-essential

---

### Post by oki-vino on 2008-03-08
Hmm..it updated some stuff when I did the apt-get, but I still get the same error. 

Thanks though!  Have any other ideas?

---

### Post by happyhamster on 2008-03-08
> **oki-vino said:**
> 
The only problem I had with installing the packages was that "x-window-system-dev" wouldn't install.Did the other packages install successfully? Else retry:

sudo apt-get install cvs build-essential bison flex-old libasound2-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev

---

### Post by oki-vino on 2008-03-08
yayyy that worked! you rock!  but now its asking me for a password. it says cvc is probably the password..but it isn't..

EDIT:

after just hitting enter key as password on third (of three) try, it output this:

--------- Error log - file /home/sean/.WineCVS/sources/cvscedega/ErrorLog : ---------
Logging in to :pserver:cvs@cvs.transgaming.org:2401/cvsroot
PAM start error: Critical error - immediate abort
Fatal error, aborting.
cvs [login aborted]: unrecognized auth response from cvs.transgaming.org: pam failed to release authenticator


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


EDIT EDIT:

Ok..tried again and again..finally it just stopped asking me for a password..*shrug*
Now it gets to "3 - Configure" and outputs this:

--------- Error log - file /home/sean/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/sean/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by happyhamster on 2008-03-08
Ok, I got curious and I'm installing as well now :D

BTW, are you sure you typed the password right (cvs not cvc).

- Anyway, the line 628: ./configure: error is because the installer expects some configuration file that you need to make in advance with autoconf. First install autoconf:

sudo apt-get install autoconf

- Next: navigate to the .WineCVS/sources/cvscedega/winex folder (presumably  in your home dir):

cd ~.WineCVS/sources/cvscedega/winex

- And run autoconf:

autoconf

- Retry running the script. If everything goes well, it will start compiling (which will probably take 30-50 minutes on an average machine).

---

### Post by oki-vino on 2008-03-08
after much consternation and like 4 more erros..its configured. THANKS!...
but im stuck on one part. when I type "cvscedega" it says it doesn't exist. there is a cvscedega folder in ~/.WineCVS/installs/ but according to the guide it should be in Home...  this is such a headache..

---

### Post by happyhamster on 2008-03-09
If everything went well, there should be a 'bin' map in your home dir containing the cvscedega script.

> this is such a headache..
It's more complicated than a regular wine installation, I agree. Is there a particular reason you're trying cvscedega instead of wine?

---

### Post by oki-vino on 2008-03-10
Well..I kind of got it working. I got it installed but when I type cvscedega I get this error:

cvscedega Features:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:    cvscedega regapi <regfilename.reg>
Install .reg with regedit:   cvscedega regedit [regfilename.reg]
Install a .dll with regedit: cvscedega regsvr32 [filename.dll]
Start winecfg:               cvscedega winecfg
Log to file:                 cvscedega log <normal params>
         eg:                 cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console
 
err:virtual:is_memory_manager_disabled could not retrieve the module file name (reason: 'bad module')
err:client:is_scheduler_disabled could not retrieve the module file name (reason: 'bad module')
Cedega CVS

Usage: /usr/lib/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests
sean@sean-desktop:~$ ERROR: wineserver exiting unexpectantly!



I dunno..I'm trying to install it because I heard its better for playing games than Wine. Is this not true? I already got Magic the Gathering Online and ITunes working with Wine..maybe I should just forget about cvscedega

---

