---
title: "vlc media player as default?"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by saru411 on 2007-05-11
this time i have installed vlc media player via synaptic package manager. it runs if i open it as a program and then open files threw it, but i cann't get it to appear when i right click video files. it only brings up the media player that comes standard,which by the way doesnt have any worthwhile codecs installed in it(i hate installing codecs, hence my favorite media player is vlc) 

i want to be able to open vlc media player by right clicking on a file and selecting run in vlc.

also when i set vlc to full screen the top and bottom tool bars for gnome dont get covered. i remember this being an issue on my last install but i got it to work properly. i just cannt remember how i did it(although i believe it was by installing it manually, but im trying to use synaptic whenever possible)

thanks again community, you keep my hair from falling out =)

---

### Post by williammanda on 2007-05-11
> also when i set vlc to full screen the top and bottom tool bars for gnome dont get covered. i remember this being an issue on my last install but i got it to work properly. i just cannt remember how i did it(although i believe it was by installing it manually, but im trying to use synaptic whenever possible

There is a known bug but not sure of any fix yet. I forgot the actual post explaining it.
Thanks

---

### Post by RTrev on 2007-05-11
> **saru411 said:**
> this time i have installed vlc media player via synaptic package manager. it runs if i open it as a program and then open files threw it, but i cann't get it to appear when i right click video files. it only brings up the media player that comes standard,which by the way doesnt have any worthwhile codecs installed in it(i hate installing codecs, hence my favorite media player is vlc) 


Right click on a file of the type you want VLC to handle from now on, like an MP3 or whatever.  Go down to properties and left click on that.  When the properties screen opens, go to the tab called "Open with."  Pick VLC.  Do this for each type you want VLC to handle.

---

### Post by saru411 on 2007-05-12
the problem rtrev is that when i right click>open with> there isnt any vlc media player to choose

---

### Post by RTrev on 2007-05-12
> **saru411 said:**
> the problem rtrev is that when i right click>open with> there isnt any vlc media player to choose

Ah.  That *is* a problem.  I've never had that happen.  Perhaps an uninstall, a re-install, and a reboot?  I have no idea what triggers the menu to include VLC or not in the choices, but I can only guess that some component might not have gotten installed correctly?

---

### Post by RawMustard on 2007-05-12
> **saru411 said:**
> the problem rtrev is that when i right click>open with> there isnt any vlc media player to choose

I've got that problem too, I just click the add button and then expand the "Use custom command" bit at the bottom of the properties window and type in vlc :)  Works for me!

I think Gnome is extra buggy in Feisty with it's right click menu, I'm having all sorts of stupid issues popping up all the time :(

---

### Post by weedenbc on 2007-05-19
I used the above to make vlc the default for files on my ubuntu laptop.  However, when I try and play a file on a network share (specifically a windows fat32 share) it still tries to use the ubuntu install default player and not vlc.  Of course no codecs are installed so it won't play.

Is there a different setting to make vlc the default for playing files over a lan?

---

### Post by dmg025 on 2007-05-21
Bumpitty Bump.  I am having the same Problem on Ubuntu Studio.   Someone please help me.

---

### Post by stchman on 2007-05-21
Works fine on both my installs of Feisty.  I just right click and select "Open with VLC Media Player" and it works.  I can select properties and that file type will always open.  Check to see if any of the hidden files in your home directory are locked.  When I installed K3B the .kde folder was locked and root was the owner so I chowned and chmod the folder and all was fine.

Yes Feisty has its quirks but all in all it does have some improvements over Edgy.  I really like that OO2.2 has way better fonts than OO on Edgy.

---

### Post by mooshimi on 2007-05-25
In order to get vlc to play fullscreen without any taskbars on your screen:

In VLC go:
Settings>Preferences

In the bottom right of the screen there is a check box "Advanced options," check it

Click on the arrow next to video
Click on the arrow next to Output modules

Click on XVideo
Check the Alternate fullscreen method box

Click on Save
Restart VLC

---

### Post by RTrev on 2007-05-25
> **mooshimi said:**
> In order to get vlc to play fullscreen without any taskbars on your screen:

In VLC go:
Settings>Preferences

In the bottom right of the screen there is a check box "Advanced options," check it

Click on the arrow next to video
Click on the arrow next to Output modules

Click on XVideo
Check the Alternate fullscreen method box

Click on Save
Restart VLC

It's funny timing, but I was playing with these very settings not 20 minutes ago.  I must admit I'm quite confused at this point.  You seem to know what you're doing, so perhaps you can help?

First, I have an nVidia 7300 GT card with 512K and dual digital outputs, running two Viewsonic Q20wb flat screens using Twinview.  I have the "restricted" nvidia driver installed, and it's working well.  Running glxgears -info shows me about 4600 frames per second, and I can slightly over-clock the card to get that to about 6500.

Watching a DVD movie using VLC, however, is "okay", but not great.  There is a bit of blurring, and occasionally the movie simply stops for a couple or three seconds and then resumes.  I'm running 32-bit Ubuntu on an AMD X2 3800+ with 2G of RAM, so I don't think I have a problem with horsepower.. and everything else happens instantaneously on this box.

When I go into VLC preferences, I check the "Advanced Options" box, and then open the "Video" menu and select "Output Modules", it says "Default."  Because I have two monitors, I was able to figure out which one it was using by default by setting each one in turn to use the second screen for full-screen mode.  It turns out that it's using the "XVideo" module.  Now, having the options of "OpenGL" and OpenGL(GLX)" makes me thing that with the nvidia card and driver that one of those would be the module I would want, but it actually looks worse when I change to either of those.  Is it normal and correct that it would choose "XVideo" by default?  Is there any way to improve the performance with this setup?

As an aside, if it makes a difference diagnostically, I have full screen video with no window borders.. and checking "Alternate fullscreen method" makes no difference that I can see.  From the tooltip hints, it looks like I'm better off without the "Alternate" method unless I need it.

It's probably also worth noting that the video is actually pretty good, especially when I set the aspect to 16:10 which seems about right for a monitor running at 1680x1050 native resolution.

Oh, my wife just stopped up and said that she thought my problem was that DMA wasn't enabled on my DVD drive.  She wasn't sure how to set it, though.

Any thoughts would be greatly appreciated, as this is driving me nuts!  Thanks...

---

### Post by lollikerwin on 2007-06-03
About right-clicking to "Open with VLC media player" as default, what worked for me is to add

video/mp4=vlc.desktop
video/flv=vlc.desktop

to ~/.local/share/applications/defaults.list in order to make this the default for mp4 and flv files, which did not previously have VLC as an option when you right-clicked on the files.

---

