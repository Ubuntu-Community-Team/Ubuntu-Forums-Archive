---
title: "game will not run"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by belikin on 2008-06-12
Hello everyone

i have installed the game ThinkTanks onto my machine.  When i try and run the game a black screen comes up for a split second and then disappears.  After that nothing happens.

a friend told me to get the latest nvidia dapper but i do not see one for my version (8.04).  can i get this in the packet manager? I really have no idea if this is even the problem.

I'm new to Linux as the coffee beans indicate and any help would be appreciated.

AMD Athlon™ 64 processor 3700+ 
1024 DDR dual channel memory 
Nvidia 7600GT
Dual boot Ubuntu 8.04 Kernel 2.6.24-16/ Windows XP

---

### Post by Kilz on 2008-06-12
> **belikin said:**
> Hello everyone

i have installed the game ThinkTanks onto my machine.  When i try and run the game a black screen comes up for a split second and then disappears.  After that nothing happens.

a friend told me to get the latest nvidia dapper but i do not see one for my version (8.04).  can i get this in the packet manager? I really have no idea if this is even the problem.

I'm new to Linux as the coffee beans indicate and any help would be appreciated.

AMD Athlon™ 64 processor 3700+ 
1024 DDR dual channel memory 
Nvidia 7600GT
Dual boot Ubuntu 8.04 Kernel 2.6.24-16/ Windows XP
To run games you will need the proprietary nvidia drivers from nvidia. The easiest way to get and install them [is with Envy.]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by belikin on 2008-06-12
Thanks for the help. did as requested and there was no problem using envy. It is an easy way to nivdia drivers.

I'm still having the same problem. I took two separate screen shots while this is happing, again it is so fast that it took me a couple of tries to get these.

The dark window is when i try to run the game.

The second is a shot of the terminal window as it is flashed upon the screen when the game is run in the terminal window. in this shot it does say something about a "locking assertion error"

AMD Athlon™ 64 processor 3700+
1024 DDR dual channel memory
Nvidia 7600GT
Dual boot Ubuntu 8.04 Kernel 2.6.24-16/ Windows XP

---

### Post by Kilz on 2008-06-12
Where did you get this game?

---

### Post by belikin on 2008-06-12
it is from garage games.  its a four year old game with simple graphics.  I have been playing almost the entire time it has been out and im finally trying to make the upgrading.

---

### Post by Kilz on 2008-06-12
> **belikin said:**
> it is from garage games.  its a four year old game with simple graphics.  I have been playing almost the entire time it has been out and im finally trying to make the upgrading.

It looks to be a 32bit game. You will need to install ia32-libs and possibly ia32-libs-sdl.

---

### Post by ddales on 2008-06-13
One quick suggestion on the Nvidia drivers.  In my opinion the best way to install the drivers is through the menu.

System > Administration > Hardware Drivers

You should see an entry for the Nvidia Drivers.  Just check the radio button to enable the drivers.  They get downloaded and installed without issue.  I would also recommend installing the nvidia-settings package which makes configuring your card and monitor pretty easy.  One thing you have to do in order to use the Nvidia Settings app is to grant permissions for either your group or your user on the /etc/X11 directory for it to work.  Otherwise, it can't save the config file.

As far as the game goes, follow Kilz advice with the 32bit libraries.

---

### Post by belikin on 2008-06-13
Thanks for the advice. i will check into both items

---

### Post by hjj5899 on 2008-06-14
> **belikin said:**
> Hello everyone

i have installed the game ThinkTanks onto my machine.  When i try and run the game a black screen comes up for a split second and then disappears.  After that nothing happens.

a friend told me to get the latest nvidia dapper but i do not see one for my version (8.04).  can i get this in the packet manager? I really have no idea if this is even the problem.

I'm new to Linux as the coffee beans indicate and any help would be appreciated.

AMD Athlon™ 64 processor 3700+ 
1024 DDR dual channel memory 
Nvidia 7600GT
Dual boot Ubuntu 8.04 Kernel 2.6.24-16/ Windows XP

:KS  Yes, it is not .

---

### Post by belikin on 2008-06-15
i have made some progress with the install of ThinkTanks.

The problem was a "locking assertion failure"

I dug around and found someone else had the same problem with a game called "neverwinter nights." The fix is to change some script in the thinktanks shell file. I opened the shell file in the text editor and towards the bottom I saw this:

# first run the updater if it is there

if [ "$RUN_UPDATER" = "true" ] && [ ! -e "${GAME_HOME_PATH}/noupdate" ] && [ -x "${GAME_HOME_PATH}/update" ]
then
${GAME_HOME_PATH}/update --auto
fi

LD_LIBRARY_PATH=.:${GAME_HOME_PATH}[COLOR="Lime"]/lib:${LD_LIBRARY_PATH}[/COLOR]

export LD_LIBRARY_PATH

EXEFULL=ThinkTanks.bin
EXEDEMO=ThinkTanksDemo.bin

I deleted what i have colored in green and the game would load and play in demo mode. I have no idea what this is or what it does but removing it did get the demo version of the game going for me.

The demo version works fine unless it is put it in full screen. If i choose to put the demo into full screen the computer freezes up and need to power it down with the power button.

Using the full version of ThinkTanks a black screen with a centered blue box stating Analog out of range 81.3 KHz / 65hz comes on when trying to start the game. In full version I can escape from it without any trouble.



The 32 bit libs could be my trouble. Do i just run the command line below in the terminal window to install them?

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

---

### Post by Cappy on 2008-06-16
> **belikin said:**
> 
I deleted what i have colored in green and the game would load and play in demo mode. I have no idea what this is or what it does but removing it did get the demo version of the game going for me.

The game is using old libraries from its own folder. I would try removing both lines,
```

LD_LIBRARY_PATH=.:${GAME_HOME_PATH}/lib:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH
```

> 
The demo version works fine unless it is put it in full screen. If i choose to put the demo into full screen the computer freezes up and need to power it down with the power button.

You can't Control + Alt + Backspace to restart X?

> 
The 32 bit libs could be my trouble. Do i just run the command line below in the terminal window to install them?

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

Yes

---

