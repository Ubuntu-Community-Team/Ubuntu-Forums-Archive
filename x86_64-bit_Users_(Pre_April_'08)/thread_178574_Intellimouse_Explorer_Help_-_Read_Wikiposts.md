---
title: "Intellimouse Explorer Help - Read Wiki/posts"
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by surroundu on 2006-05-17
Hi there,

I must be ignorant, as I've got an Intellimouse Explorer that isn't working as I'd like. The Left/Right buttons and scrolling wheel worked, but the Forward/Back buttons didn't function. So, I looked up the topic here and on the wiki and followed the instructions:

1. Modified the xorg.conf file mouse parameters to match several examples. I proof read my file and thought it was all good.

2. Installed IMwheel from Apt-get

3. Modified the imwheel (it was imwheelrc) as per the wiki and other examples

4. created the 57xmodmap file as specified in the wiki

Now, Right and left buttons work as before. Scroll wheel doesn't scroll down, but acts as a forward/back set of buttons in FF. I scroll up to go backward and down to move forward. scrolling within the page is gone, and the real Forward/back buttons are still useless.

I obviously misconfigured something- please help. (and try not to laugh)

Thanks!:-D

---

### Post by m_memmory on 2006-05-20
I had this same thing happen with my mouse.  To fix it I went back into xorg.conf and set the 

```
Option "ZAxisMapping" "6 7"
```

to

```
Option "ZAxisMapping" "4 5"
```

and I found that this worked.  The wheel worked normally (again) and the buttons would also work in Firefox.  It didn't seem to work in nautilus but I wasn't too bothered about them working there - more important to me that Firefox worked with them.

---

### Post by Dixius99 on 2006-05-20
I'm having the same problem, surroundu.

Actually, I somehow configured my mouse so that the forward and back function  was working through the scroll wheel, but only when button 3 was pressed!

I tried the fix above, and the scroll wheel works, but still no forward and back.

(I should mention that I had scrolling and forward/back working fine in Breezy, and that this seems to have stopped working properly when I upgraded to Dapper Flight 8.)

---

### Post by mmcmonster on 2006-05-27
This is starting to bug me.

I had it working in Breezy, but instead of just upgrading, I decided on a clean install (I had to do some repartitioning :().

Anyone get this to work properly?  I somehow managed to get the scroll wheel to do the forward/backward button movements, which was useless for me.

Some more experimentation, I guess.

If I do manage to get it to work, I'll post a copy of the config files for posterity. :eek:

---

### Post by mmcmonster on 2006-05-30
As promised, here is how I got it to work.  Thanks go to [ubnoobie]("http://www.ubuntuforums.org/showpost.php?p=1068222&postcount=2") and [Matt's Blog]("http://dotnet.org.za/matt/articles/39097.aspx") for the help. I have a microsoft intellimouse explorer 3.0 USB optical mouse. I got this working on the i386 version of Ubuntu Dapper 6.06 Release Candidate.

*** Modifications made on June 6, 2006:  I got XGL working on my PC now.  Interestingly enough, this broke the mousewheel support on my mouse.  The fix is the alternate step 5. ***

1. sudo apt-get install imwheel

2. sudo gedit /etc/X11/xorg.conf
  Edit the following section:
```
Section "InputDevice"
         Identifier  "Configured Mouse"
         Driver      "mouse"
         Option      "CorePointer"
         Option      "Device"        "/dev/input/mice"
         Option      "Protocol"      "ExplorerPS/2"
         Option      "Buttons"       "7"
         Option      "ZAxisMapping"  "6 7"
        EndSection

``` to look like this:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons"       "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping"  "4 5"
EndSection

``` 
3. gedit ~/.imwheelrc
```

".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right
``` 


4. sudo gedit /etc/X11/imwheelrc/startup.conf
Find this line:
```
IMWHEEL_START=0
``` 
and replace it with this line:
```
IMWHEEL_START=1
``` 

5. sudo gedit /etc/X11/Xsession.d/63xmodmap
```

 killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
 
``` 
 5. (Alternate) Instead of the above code, use the below replacement for 63xmodmap if your scrollwheel doesn't work after all the steps are completed.  This may happen latter on if you later install XGL on a machine with an nvidia graphics card.
 ```

 killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
 
``` 
 
6. sudo chmod 777 /etc/X11/Xsession.d/63xmodmap

7. Restart X:
7a: Log out from gnome
7b: ctrl-alt-backspace
7c: Log into gnome

---

### Post by ketsugi on 2006-05-30
Does anyone have a working config for the Microsoft Intellimouse with Tilt Wheel (9 buttons)?

I've tried several links and howtos, but I've never been able to get the buttons to work properly. I don't even need horizontal scrolling that badly, but I really want the forward/backward buttons to work.

---

### Post by justmehere on 2006-05-30
I've just got my side buttons working by adding just the   
  Option         "ButtonMapping" "1 2 3 6 7"
line to my xorg.conf and restarting x. You could try something similar?

---

### Post by Craig Prevallet on 2006-06-22
[QUOTE=ketsugi]Does anyone have a working config for the Microsoft Intellimouse with Tilt Wheel (9 buttons)?

I've tried several links and howtos, but I've never been able to get the buttons to work properly. I don't even need horizontal scrolling that badly, but I really want the forward/backward buttons to work.[/QUOTE]

Yes, I have the tilt function working but it requires Dapper's Xorg 7.0.   See my earlier post:

[http://ubuntuforums.org/showthread.php?t=183547&highlight=tilt](http://ubuntuforums.org/showthread.php?t=183547&highlight=tilt)

---

### Post by Brando569 on 2006-06-23
how would i get my side button to work? i have an intellimouse (not the explorer version) that just has a back button, ive used xev to figure out the mappings and it is as follows:

1-left 2-scroll click 3-right 4-up 5-down 8-side button

this is the section of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option 		"Buttons" 		"8"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

and this is my xbindkeyssrc:

"/usr/X11R6/bin/xvkbd -xsendevent -text "\A\[0xff51]""
    m:0x0 + b:6.

this is supposed to be alt-left arrow to go back a page in firefox

---

### Post by Life On Mars on 2006-11-11
This is what worked for me after trying mmcmonster's solution, which didn't work:

Changed xorg.conf section to:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons"       "7"
    Option         "ButtonMapping" "1 2 3 4 5"
    Option         "ZAxisMapping"  "6 7"
EndSection
```

---

### Post by cjoey19 on 2007-01-08
wow, working perfectly, thanks! especially for the xgl code part..

---

### Post by Skip McMahan on 2007-09-20
Thank you so much for this, I used the alternate to step 5 (nvidia card) and it works great. Thank you, this was one of the last things about ubuntu that bothered me.

---

### Post by f4rrest on 2007-11-05
mmcmonster's steps 1-5 (alt) worked for Gutsy w/ Nvidia (on 32-bit). thanks!

---

### Post by xenspidey on 2007-12-04
hey guys. i just got the scroll wheel and the back and forward buttons to work fine in Firefox without imwheel. this is my xorg.conf 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"explorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by TheBoz on 2007-12-20
So *my* big question is.... if the post from "Life On Mars" worked for me when the previous example by "mmcmonster" didn't, do I have to go back and undo all the stuff that mmcmonster told me to do? (specifically the "/etc/X11/Xsession.d/63xmodmap")



EDIT: Actually, I'm an idiot. They worked fine for me. (dang... I hate when I forget WTF I'm talking about)

---

### Post by hertzsae on 2007-12-25
xenspidey's solution worked perfectly for me after reboot.  No need to edit anything other then xorg.conf

Thanks xenspidey!

---

### Post by dwp0980 on 2008-02-18
Can anyone confirm if this works with nautilus?  I have managed to get back/forward (side buttons) working fine using similar posts (just editing xorg.conf worked for me) but I can't seem to get it to work with nautilus.

Any ideas, or does this just not work with 7.10 Gutsy?

Thanks

---

### Post by Guinness70 on 2008-03-05
xenspidey solution worked.. sorta
the side buttons work as back and forth in FireFox but the scroollwheel didnt work
but at boot i got a gnome error and now im looking at a different desktop theme.

so went back 
*sudo gedit etc/X11/xorg.conf*
changed
*Option "Protocol" "explorerPS/2"*
back to
*	Option		"Protocol"		"ImPS/2"*

and after reboot the error was gone, theme restored
but the side buttons didnt work as back and forth no more
the small side button works like the rightbutton, the large one doesnt do a thing

---

### Post by Guinness70 on 2008-03-05
```
# Left/Right & Thumb stuff
None,		Left,	Left,				7,
None,		Right,	Right,				7,
None,		Thumb1,	Down,				7,
Shift_L,	Thumb1,	Up,					7,
None,		Thumb2,	Up,					7,
Shift_L,	Thumb2,	Down,				7,
```

i cant find the logic in this. could someone explain this please.
thank you ever so much

maybe by example: i want Thumb2 to act as Home, how do i code that in this matrix?

---

