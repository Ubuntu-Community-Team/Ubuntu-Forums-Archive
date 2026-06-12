---
title: "[SOLVED] Ctrl+Alt+F1 - Nothing Happens"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by andyharney on 2008-06-20
Hi im new to ubuntu, so im finding things a little different (having swapped from Vista).

Im using a Presario V6000 with Ubuntu 8.04 (Heron), im trying to follow this post *[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)* to get the newer nVidia drivers for my card.

However when i press Ctrl+Alt+F1 my screen goes blank.  Pressing Ctrl+Alt+F7 returns me to the desktop.  However long i leave it after pressing Ctrl+Alt+F1 it stays blank.

If there is any other info that is needed please just ask.
Many thanks with this.

---

### Post by Qrikko on 2008-06-20
you don't get a new terminal? it is just black?

could you try using another one? (you have them "all the way" from F1 -> F12 I think)

I think that the F1 one is used for boot and might be "busy" or something I don't know well how it work technically, probably someone can explain that to us :)

but try use the others too.. F2, F3 and so on :)

---

### Post by andyharney on 2008-06-20
Thanks for the swift reply, yeah i've tried the others.
But to no success, my screen just goes blank, there is power to my screen because its still "lit" just nothing is displayed.

I havent got a clue where to start, total Ubuntu beginner.  And i thought i was pretty savvy with computers!

---

### Post by Qrikko on 2008-06-20
hmm.. I am really not sure.. what would happen if you do a change in run-mode? 

$> sudo /etc/init.d/gdm stop

OBS OBS OBS, it could leave you hanging without a X-server i.e. not being able to CTRL+ALT+F7 back (because the server would be shut down). This is not a major problem and if you restart the compy it will start up a new X server for you. But I am curious to see. and also sorry to ask but since you say that you are all new to Ubuntu, is it also to Linux?
And you get NOTHING at all when you CTRL+ALT+F1? like it's all black no text or nothing (pretty sure from your description but just want to make sure).

Also could you see/post any lines that start in:
(EE) or (WW) in a file called: "/var/log/Xorg.0.log"

if you do this in a terminal:
$> cat /var/log/Xorg.0.log | grep EE
and get something from it, paste it here so I can see it :)

if you don't get anything (except this line: "(WW) warning, (EE) error, (NI) not implemented, (??) unknown.")

then go on to see if you get any messages from
$> cat /var/log/Xorg.0.log | grep WW

and paste the results :)

you can if you think it is easier do this:

$> cat /var/log/Xorg.0.log | grep WW > minfil

and just because you are new and I love linux ;) I will explain what it is :P

the command cat echo the text of a file to the standard output (your screen)

/var/log/Xorg.0.log is a file that is saved which contain any Xorg related errors while initializing Xorg (your X server) and I think if there is something to be found we will find it there :)

an the pipe (|) is used to work on the result so to speak.. while grep ignores any line that don't contain the text you "search" for.. so it "pipes" the result to the command grep which see too it to only echo lines where this text occur.

the > redirect the standard output from being your screen to a file named "minfil" in the directory you are.. so after it you can do "cat minfil" or "gedit minfil" to see the result.

if you feel very confused now.. then just post your /var/log/Xorg.0.log and accept my apology if I got to technical :)

---

### Post by Qrikko on 2008-06-20
so just to sum it up and make a more "easy to read" post.

can you check if you have any (EE) or (WW) in the beginning of any line in the file: "/var/log/Xorg.0.log" :)

---

### Post by andyharney on 2008-06-20
Yes im new to Linux too! Your right with what your saying, the screen is just blank, nothing displayed.

I ran > $> sudo /etc/init.d/gdm stop, and my display went blank. after about 5 minutes i restarted my machine as Ctrl+Alt+F7 didnt do anything.

After runnning > $> cat /var/log/Xorg.0.log | grep EE I get this-
[I](WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER[/I]

After running > $> cat /var/log/Xorg.0.log | grep WW I get this-
[I](WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(WW) Configured Mouse: No Device specified, looking for one...[/I]

I think i know why i get the above message, i have connected to my laptop via SVGA my 32" TV.  The TV displays Ubuntu when booting up but after the boot up screen it goes blank.  This is a seperate issue i'm gonna try an fix later!

---

### Post by Qrikko on 2008-06-20
Damn that's a nice and clean post if I wrote like that I could become president or something o.O :)


well.. I don't think it is "related" or.. well I don't know :P but the warnings you get from the nVidia thingies feel like it has nothing to do with that you can't go into a different run-level <-(is it true.. I think that it is what you do basically but I might have the terminology wrong there)..

I think someone with a bit better knowledge have to help you sort it I am afraid. I know there are people here that have a great knowledge, and I feel I can't figure out something more to try.. though.. it was kind of a bad idea to check Xorg.0.log in the first place I guess.. the problem isn't in your X it is in the parts not concerning X I take it..

Better let someone with more experience help you figure this one :P or I will just help you break your system ;)

---

### Post by andyharney on 2008-06-20
I think the clean post stems from writing countless military reports, where the reader may mis-interpret something!

I appreciate the help given so far, no doubt the first of many questions i've yet to answer.

Yes i think it is a different "run-level".  The post mentions something about "killing" X to unload the drivers.

---

### Post by nikgare on 2008-06-21
>>However when i press Ctrl+Alt+F1 my screen goes blank.

Maybe you monitor is not adjusting to the right resolution and there is stuff there, but off the screen.  Try pressing "Auto" on you monitor or adjusting the display with the other buttons.

---

### Post by Qrikko on 2008-06-21
now that is a good point :) would it mean you could "blind login" and "blind xinit"?

could test that if the screen can't adjust.. and if it isn't very stupid idea ;)

---

### Post by andyharney on 2008-06-21
I am using a laptop, there is no Auto button unfortunately.

I am unsure what "blind login" & "blind xinit" are, but willing to give it a try.

---

### Post by Qrikko on 2008-06-21
Ah, I just meant to try to type your username, password and hope that without seeing what you are doing you logged in :)

and after it type:
$> xinit
(or)
$> startx
(or)
$> gdm

to see if it initialize X if that is the case then it is indeed the mentioned problem that your screen for some reason can't adapt to the resolution change.. if you have all the other functionality..

well it's at least something to try I guess :)

---

### Post by andyharney on 2008-06-21
Ok, before I give that a try.

I type my user name, hit enter, type my password, hit enter.

Then type> $> xinit
(or)
$> startx
(or)
$> gdmIf thats correct then i'll give it a shot.

---

### Post by Qrikko on 2008-06-21
that wasn't too cleaver of me..
I just realized that you will have a x server runnign already

instead of the xinit thingie..

do this:

(after logging in without seeing)
type:

file a > b

and then go back to your tty7 and check if the file was created

(it is in: ~/b in that case)
(and ~/ = your home directory for the user you logged in with)

---

### Post by Qrikko on 2008-06-21
so step by step what I was thinking:

type username *enter*
type passwd *enter*

*count to 5*

type:
file a > b

go back to graphical interface and check for

~/b

---

### Post by andyharney on 2008-06-21
That does exactly as you say.  I get "b".  It seems that my screen wont support whatever resolution is loaded whenever i press Ctrl+Alt+F1.

---

### Post by Qrikko on 2008-06-21
AND more importantly that we are getting somewhere :)

then we know what the problem is :)

did you say what card you use? hmm.. I have some resolution problems on my Ati Xpress 200M.. (aka. the trouble maker :P) but only with the newest ATI drivers (8-6) it have never been a problem like this one you have.

and the problem I have now is that the resolution get wrong (corrupt with MAJOR artifacts) when I switch back to tty7.

so.. hmm.. what can be done about you problem then..? I don't know about it right now.. but if you switch during boot (i.e. press CTRL+ALT+F1 while the ubuntu loading screen is showing (just after grub loaded)).. do you see the information then?

it is a list of modules that it loads.. if you see this one and then when it is done it does a correct switch to the X server when it initialize GDM..

I am not sure what it will help to know :P but well the more info we have the easier it feel to get some answere :)

I will also try to Google some more on it now that we know at least what the problem is :) (i.e. that it's hardware and nothing to do with software... probably :P)

---

### Post by andyharney on 2008-06-21
My graphics card is a nVidia GeForce GO 6150.  Im trying (hence encountered this problem) to update my drivers.

I tried Ctrl+Alt+F1 whilst my machine was booting up and it worked fine.  Once booted up it reverts and I can login fine.

It does have a feeling of a hardware problem.  And to make things worse for the moment my internet is down, having to post this via the mobile!

---

### Post by Qrikko on 2008-06-21
Ah, well I don't know toooo well about the nVidea drivers :/ but I know that they:

1) should be better supported then the ATI once (but thanks ati for actually doing some kind of a leap toward better support, it is getting along pretty nice)

2) and more importantly that you could install them using envy(envyng if you are using Hardy) ^^

Envy is a script for handling nVidea and ATI vendor versions of the drivers (fglrx at least on ATI, I am not sure about the terminology for nVidea so I try to keep a bit reserved that there can be differences) 

And Envy is if nothing else a great way to get your installation for the drivers correct. I know that there can be some problems on ATI at least, and Envy does the whole thing, it download the driver (might be a version after the absolute newest but wait with that one for a little :)) and it remove and do an installation which is correct so you can be pretty sure that you will have a working graphics driver after the Envy installation at least, and after it it might be easier to update to the newest version or if you are happy with the Envy version then cheers. :)

To set up envy you just get it off the repos, if you are using Hardy and Ubuntu (i.e. Gnome, (not Xubuntu, Kubuntu...)
```

$> sudo apt-get install envyng-gtk

```

and if you are using any other (ku-, xu-, ..., -buntu)
```

$> sudo apt-get install envyng-qt

```

then from terminal you can run:
```

$> sudo envyng -g

```
(obs it take either a -g or a -t flag, it's needed and tell if you are going to use the 'g'raphical or 't'ext interface, they are almost identical so just choose one, ah and also just so you know.. you have to run envy as super user)  :)

then it is really easy to follow.. in your case.. basically choose nVidea and hit go and wait while Envy take care of a lot of work for you :)

This is a nice way to ensure you have the vendor version drivers installed correctly.

for full information and if you are using any other distro (I think you said you are using hardy, but for the older distros I think you need to use "envy" rather then "envyng" but if you want to know more here is the page of the script:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

OBSERVE THAT THIS is if you (as I) suspect that there could be something strange with the driver installation, but it can also be something with hardware / driver combination I guess.. like I said, on my system everything were a breeze with switching between the tty when I used ati's 8-5 driver, but when I updated to 8-6 I got a problem to change back into the gui from another tty, and I have to do a CTRL-ALT-BACKPACE to fix it (I am fairly sure it is a problem in setting the resolution), but it's not really a problem to me since I don't switch out of my gui very often.

Well hope you can skim through and find some nice parts there I think that Envy is nice to know about at least. :)

---

### Post by will.first on 2008-06-22
I had the same problem with my HP DV-9010 after I upgraded from Feisty to Hardy. No switch to a console using Ctl-Alt-Fn. I tried everything I could find in the forums posts with no success.  When nVidia released their drivers version 173.14.05, I found this in the fix list:

"Fixed a regression causing some GeForce 6100/6150 systems to fail to restore the screen after DPMS cycles."

Mine is a 6150.  I took a chance that the annoying DPMS restore annoyance (which made suspend restores work badly for me) might be related to the mode switch problem when switching to a text console so I tried it.  That driver indeed fixed all the problems.  There is another release since then that I have not yet upgraded to.

Something you must beware when using the nVidia site drivers:  Load the Ubuntu "nv" driver first and reboot, then be sure to completely uninstall, remove, and blacklist the restricted drivers.  The nVidia install only runs properly in a text-mode console with X stopped (on all consoles).

Final warning, kernel updates will break X forcing you rebuild the driver for each new kernel so keep your latest nVidia installer readily accessible.  I think there's a shortcut around this, but I rebuild each time to be sure everything is version consistent.

Good luck, I hope this helps.

---

### Post by Tomatz on 2008-06-22
It should be** ctrl alt F3** but if you have tried that maybe your card/x server cant detect the correct resolution when you stop the x server and drop to the cli. Resulting in a blank screen.

I would suggest that you just use envyng as it installs the latest nvidia drivers for you automatically.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

;)

---

### Post by andyharney on 2008-07-07
Sorry for the late reply, just returned from 2 weeks in Kefalonia. Lovely Stuff.

I've ran envy and it worked like a dream.  Now i can do what i couldn't do before.  I can access the console.

Thanks guys, much appreciated.

---

