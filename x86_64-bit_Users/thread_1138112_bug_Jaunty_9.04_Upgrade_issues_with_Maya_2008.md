---
title: "bug: Jaunty 9.04 Upgrade issues with Maya 2008"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by Kryptick on 2009-04-26
Welp I did the upgrade on the 64bit box (and the 32bit laptop) and both systems are no having problems in Maya 2008 which never happened in 8.10
The Problem:
Maya gets `stuck' in an input mode like you were holding down a key on the keyboard continuously...

example:
Renaming objects in maya causes the keyboard to get trapped and a beeping noise happens due to the repeating `keypress' which can be cleared by selecting the mel input area at hte bottom and tabbing over to the script editor area then back to the opengl window
very obscure.
Also when smooth skinning it captures the b key more often than not and the same thing helps clear the issue

Not entirely sure wth is going on here or what changed that would mess with maya 2008 like this but pre the upgrade everything was working just fine (ie everything was installed properly etc)

If anyone might have a great educated guess ...

Thanks
James

EDIT 11/01/2010:
_____________________________________
can't seem to post into this anymore;
for 9.04 and higher here is the solution for the keyboard errors as provided by ragtag further in the thread

> Open gconf-editor
Set /apps/gnome_settings_daemon/plugins/a11y-keyboard/active to false.

This seems to fix the problem.

Getting base fonts in maya's text editor as provided by agibli further in the thread
> In any case, the following command fixed it for me:
Code:

sudo apt-get install t1-xfree86-nonfree

This will install a handful of fonts that Maya can use, including Courier.

---

### Post by lemmyg on 2009-04-28
Hi, I have the same problem. but no solution is possible.
I hope someone finds a solution.
Thanks.

---

### Post by Kryptick on 2009-04-29
Do you use a wacom per chance?

---

### Post by lemmyg on 2009-05-01
Hi, I have one but I have not tested. I think it works well. In any case, I think that has to do with this problem. I think that problem is deve to updated the Xorg 1.6 and surely that which is causing problems.

---

### Post by Kryptick on 2009-05-01
Yeah I removed my wacom drivers and unplugged it and the same thing was happening
Have also put compiz back on and tested that out same thing
And same with compiz removed....

Funnily enough Jaunty 9.04 seems to perform better all round with compiz installed, (just can't use the damn hotbox in maya or all hell breaks loose *sigh*)

Other than that I'd say we're def facing a legit bug here (difference from 8.10) that is causing the problem, and I can't for the life of me get a bug report to go into the system properly ...
doh

---

### Post by lemmyg on 2009-05-02
Hi, I tried to install kde desktop and not has the problem. The bad thing is that I'm too accustomed to using gnome. I will continue waiting a fix.

---

### Post by jezscha on 2009-05-07
Hi, I have the same problem. 
Please can you anybody fix it or to find a solution for it. 
It seems it's doing it always after i used the keyboard shortcut <Tab>+<alt> for switching of application. 
The only way how to stop it was to switch-off <numlock> and then key any of the arrow keys on num-pad...

Anybody have any suggestion? Cheers!

---

### Post by jezscha on 2009-05-17
hi, have you anybody found a solution for that? i found it very annoying to not be using that <alt>+<tab> shortcut... 

Anyway I noticed that it's also starting the "repeating process" if i was changing any of values in the Channel box and then confirm them by the <Enter> key..

It's better to use <tab> for confirming..

---

### Post by kougaru on 2009-06-03
This issue is also affecting me. Sadly I don't have any new info about it. Everything seems to be covered pretty well here. 

I had to switch to Kubuntu to avoid the issue but KDE4 is so unstable Maya is crashing more often then it was in Gnome.

---

### Post by jspatrick on 2009-06-24
I'm also having this problem in Maya 2009.  I noticed it when I tried to type a command into the command line and hit enter - then the enter key was as if it was stuck, which I noticed because when I tried to switch back to gedit it kept entering new lines.  I was also having issues related to this when trying to rename nodes...this is a pretty bad bug that's making Maya borderline-unusable for me!

I would be completely willing to help try and track this down, but I've only been using Linux for about a week...so, err, I could at least help test solutions anyone might propose.  If anyone has any suggestions, please let me know!

---

### Post by Kryptick on 2009-06-24
I've dropped back to 8.10 way too many issues in 9.04 for production
videos don't play properly
sound issues
the maya stuff 
etc etc

will wait a few more months of updates etc before I bother checking out the next version again and in future won't be so fast to click the upgrade button :)

---

### Post by lemmyg on 2009-06-24
Hi, 
	
[LEFT]I am using xfce4. It works well and is a simple desktop. For now, there is no other suloción, but I think that the solution soon.
It seems that this is a problem in some component of gnome. 
Patience.[/LEFT]

[https://bugs.launchpad.net/xorg-server/+bug/367136]("https://bugs.launchpad.net/xorg-server/+bug/367136")

---

### Post by Mikael P. on 2009-07-01
This is driving me nuts. It occurs more in certain instances for some reason.
In that bug report they said that turning off keyboard repeat would alleviate the issue, but I see no difference.
If someone has a solution, I am all ears!

---

### Post by lemmyg on 2009-07-01
Hi Mikael,
There seems to be a component of Gnome which is generating problems with autorepeat. This only happens in Gnome. In KDE and Xfce4 does not happen. This is reported in Launchpad and bugzilla.gnome.org.

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136)

[http://bugzilla.gnome.org/show_bug.cgi?id=587229](http://bugzilla.gnome.org/show_bug.cgi?id=587229)

	
I think it's the gnome-settings-deamon. If you disable the gnome-setting-deamon, the problem disappears. You can disable in gnome-session-properties.

	
My advice is to disable the process or you can use xfce4, until gnome confirm the problem and solve it. This may take some time.

---

### Post by Mikael P. on 2009-07-02
hm ok. Good to know atleast where it comes from.
I am really new to all this, so where do I find this gnome-settings-deamon? I read about it before posting, but couldn't find it.

Someone else spoke of using an accessibility tool to help. By turning on bounce keys you can get rid of the repeats too.

I have to check out this xfce4 you mention. Thanks for the reply!

---

### Post by lemmyg on 2009-07-02
Hi,
to disable the gnome-settings-deamon, you have to run this command in a terminal:

gnome-session-properties;

Is the application to configure what process to start on login.The problem is that gnome initialised with the default settings. 

The other option, is install kubuntu desktop(xfce4). Is a simple desktop and woks well. This is the option what I'm using. Also works with kde4, but install too many things and is less stable. I prefer xfce4.

in a terminal run:

sudo apt-get install kubuntu-desktop;

and then, start session with this desktop.

good luck.:smile:

---

### Post by Mikael P. on 2009-07-03
Thanks for the explanation. Will try that out. Right now with no keyrepeat and bounce keys things are working moderately well. I'll dig into this once I am off work.

---

### Post by agibli on 2009-07-05
I'm definitely interested in seeing a proper solution to this. Right now the approach I've taken is to kill the gnome-settings-daemon process whenever Maya starts and then relaunch it when Maya is closed (I had already used the same approach to temporarily disable compiz, so it seemed to make sense). Not an ideal solution by any stretch of the imagination.

Is there a command I could use to just disable auto-repeat or enable bounce keys?

---

### Post by Mikael P. on 2009-07-14
Hey again,
**agibli**, have you created some kind of automatic script to kill those things whenever you run maya?
How do you temporarily disable compiz? I thought that I could do that by saving different pref files, but it gladly deleted my prefs when I told it to revert to default. I did that because I switch between no visual effects and normal visual effects in my apperance settings. I would gladly live with no visual effects if the screen wasn't flickering when I am using it.

I don't know about switching window manager as I am getting comfortable with gnome and don't want to spend too much time configuring these things.

---

### Post by agibli on 2009-07-14
> **Mikael P. said:**
> Hey again,
**agibli**, have you created some kind of automatic script to kill those things whenever you run maya?
How do you temporarily disable compiz? I thought that I could do that by saving different pref files, but it gladly deleted my prefs when I told it to revert to default. I did that because I switch between no visual effects and normal visual effects in my apperance settings. I would gladly live with no visual effects if the screen wasn't flickering when I am using it.

I don't know about switching window manager as I am getting comfortable with gnome and don't want to spend too much time configuring these things.

Hey Mikael,

Disabling compiz is done with the command **killall compiz.real**, and restarting is done with **compiz --replace**. It turns out that at least on my system, simply having the compositing extension enabled in Xorg doesn't cause any problems in Maya. Having a compositing window manager running does, however.

I've been using the following script to launch Maya. It's worked out okay for me, but of course, your mileage may vary:
```

#! /bin/bash

killall compiz.real
killall gnome-settings-daemon

/usr/autodesk/maya/bin/maya

if [ -z `ps -e | grep maya.bin` ]; then
    gnome-settings-daemon
    compiz --replace
fi

```

---

### Post by Mikael P. on 2009-07-14
That was handy! Thanks a lot for that little script. It works great here.
Now I have the same question as you, how do I change the keyboard settings with a command.

---

### Post by agibli on 2009-07-15
> **Mikael P. said:**
> That was handy! Thanks a lot for that little script. It works great here.
Now I have the same question as you, how do I change the keyboard settings with a command.
Glad to hear it worked for you.

Speaking of commands to change keyboard settings, I have to warn you. When I was looking for a way to disable key repetition, I came across the command "xset r off"... *do not use this command while gnome-settings-daemon is running* *or bad things will happen*. So there goes my idea of disabling key repetition so I don't have to kill gnome-settings-daemon.

---

### Post by Mikael P. on 2009-07-15
Yeah I read about that command. When they talked about it they suggested having a second shell open with the command to get rid of it pre-written so you would get out of the loop by pressing return there.

---

### Post by lemmyg on 2009-07-21
Hi, 
I have new problem, jeje.
when I try to create 3D text.
using the command
textCurves-ch 0-f "Courier"-t "Test";
Maya returns this error
Error: line 1: Unable to open postscript font file for Courier
Apparently, Maya not find the fonts.
Any suggestions?
Thanks in advance.

---

### Post by agibli on 2009-07-21
> **lemmyg said:**
> Hi, 
I have new problem, jeje.
when I try to create 3D text.
using the command
textCurves-ch 0-f "Courier"-t "Test";
Maya returns this error
Error: line 1: Unable to open postscript font file for Courier
Apparently, Maya not find the fonts.
Any suggestions?
Thanks in advance.
Funny you should bring that up, I had the same problem and didn't decide to fix it until this morning.

I haven't investigated enough to pin down the exact cause of the problem, but my guesses so far have been: Maya looks for fonts in /usr/X11R6/lib/X11/fonts/ instead of /usr/share/fonts/, only supports Type1 fonts, or even worse only supports ASCII Type1 fonts.

In any case, the following command fixed it for me:
```
sudo apt-get install t1-xfree86-nonfree
```This will install a handful of fonts that Maya can use, including Courier.

---

### Post by lemmyg on 2009-07-21
Fixed.
Thank you very much.

---

### Post by tempo500 on 2009-07-23
this bug is anoying! i dont have the time to downgrade so i am using ubuntu without gnome-settings-daemon. i tryed xcfe, which i liked, but an unstable maya is no good at all. hope this gets fixed soon! thanks, phil

---

### Post by Mikael P. on 2009-07-23
If you run this command for starting maya:

```

! /bin/bash

killall compiz.real
killall gnome-settings-daemon

/usr/autodesk/maya/bin/maya

if [ -z `ps -e | grep maya.bin` ]; then
    gnome-settings-daemon
    compiz --replace
fi

```
Someone else gave me the tip of using it.

Then you get rid of those nasty issues.

---

### Post by wubi on 2009-07-30
> **Mikael P. said:**
> If you run this command for starting maya:

```

! /bin/bash

killall compiz.real
killall gnome-settings-daemon

/usr/autodesk/maya/bin/maya

if [ -z `ps -e | grep maya.bin` ]; then
    gnome-settings-daemon
    compiz --replace
fi

```
Someone else gave me the tip of using it.

Then you get rid of those nasty issues.

I apologize as I'm still a linux Noob How would run this script before launching Maya?

Cheers.

---

### Post by agibli on 2009-07-30
> **wubi said:**
> I apologize as I'm still a linux Noob How would run this script before launching Maya?

Cheers.
No apology necessary, I'm not sure who among us considers themselves an expert but I ain't one. That said, there being various shades of noob, I'll err on the side of being overly simplistic with these instructions:

[LIST]
[*] Save the code as a script file (e.g. /home/yourname/maya/launch_maya.sh) with a plain old text editor.
[*]In your file browser, right click on the script file and go to Properties. Under the "Permissions" tab, check the box that says "Allow executing file as program."
[*]Go to System > Preferences > Main Menu. Click on "Graphics" in the left panel. Maya should then be listed in the right panel.
[*]Select the entry for Maya and click the "Properties" button. In the "Command" field, type the file path to the script you just created.
[/LIST]
That should do it. Also, I figure I should note the two main problems I've encountered with this script, both seemingly having to do with killing gnome-settings-daemon. First, my GTK theme is sometimes not restored when Maya exits, usually if it's been running for a while. Secondly, for me it usually crashes gnome-do, so it may have similar conflicts with whatever software you're running.

---

### Post by tempo500 on 2009-07-30
the script is working for me just fine, i remove the compiz stuff because its commented out in the xorg.

i still hope this will get fixed! all those weird sound schemes and i like my dark theme, i even have mayas gui colors in a dark tone, so i guess it should be possible for gnome. :-)

---

### Post by babygenius55 on 2009-08-30
Worked like a charm for me as well.  Is there any more info on a permanent fix?

BTW I made a launcher shortcut for my the script in Cairo-dock, and haven't looked back.

I love you guys.

Now to test the hotbox...I will edit again if it works, if it doesn't I have to logout

HOTBOX works baby!  Why I couldn't find a reference to this script when looking for the answer to the hotbox problem is frustrating, but it's going good now.

---

### Post by ragtag on 2009-09-03
Open gconf-editor
Set /apps/gnome_settings_daemon/plugins/a11y-keyboard/active to false.

This seems to fix the problem.

---

### Post by lemmyg on 2009-09-03
Finally, it works perfectly. Now, there's no need to use scripts to start Maya. Please, can you report at

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136)


Thank you very much.

---

### Post by lemmyg on 2009-09-03
Sorry, report in 
[http://bugzilla.gnome.org/show_bug.cgi?id=587229](http://bugzilla.gnome.org/show_bug.cgi?id=587229)

---

### Post by agibli on 2009-09-03
> **ragtag said:**
> Open gconf-editor
Set /apps/gnome_settings_daemon/plugins/a11y-keyboard/active to false.

This seems to fix the problem.
Hey, that certainly seems to do the trick. Thank you so so much, this problem has been bothering me for a while now.

Of course that plugin should probably be fixed, but I doubt it does anything I can't live without.

---

