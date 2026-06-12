---
title: "seperate x server"
date: 2008-10-02
forum: Wine
---

### Post by luposolo on 2008-10-02
does anyone have a up to date tutorial on how to run wine games and native games in a seperate x server

---

### Post by luposolo on 2008-10-02
wow 60 minutes and no reply

---

### Post by luposolo on 2008-10-03
i guess the guru's aren't on to answer my question

---

### Post by naesa on 2008-10-03
I'm not the guru you ask for but i'll have to ask: What's wrong with the current one posted in sevral threads in this forum?

---

### Post by Thelasko on 2008-10-03
It doesn't work for me either.  I'll spare the details for fear of hijacking the thread, but I think it has to do with the X server changes made in Hardy.

---

### Post by luposolo on 2008-10-03
i used this script called Xswitch so i could play games on a seperate x server and i didnt get any speed increase what so ever maybe im doing something wrong but from what ive heard you are suppose to get a enormous frames per second boost from using these scripts

---

### Post by Thelasko on 2008-10-03
Is it anything [like this?]("http://ubuntuforums.org/showpost.php?p=3908174&postcount=2")

---

### Post by Dark9204 on 2008-10-04
Will that script really give any performace increase? i dubt it will, this script is made to aoid screenlets and desktop effects, but it will do that anyway in the background, so whats the point? This was made for testers and debuggers to not screw ut there X server and being forced to restart it again.

I run Ubuntu with no visual effects, and noticed a huge FPS increase compared to having the visual effects and screenlets on

---

### Post by Thelasko on 2008-10-06
> **Dark9204 said:**
> Will that script really give any performace increase? i dubt it will, this script is made to aoid screenlets and desktop effects, but it will do that anyway in the background, so whats the point? This was made for testers and debuggers to not screw ut there X server and being forced to restart it again.

I run Ubuntu with no visual effects, and noticed a huge FPS increase compared to having the visual effects and screenlets on
a) We are trying to make the script work, not debate it's merit.
b) [It does]("http://ubuntuforums.org/showpost.php?p=3908465&postcount=6") increase performance.

The point of this script is to get any unnecessary parts of xserver out of video ram.  If you are happy with your performance as is, don't use this script.

---

### Post by DaVince21 on 2008-10-06
You know what would increase performance most? Shutting down *any* graphical session and purely run an X session for whatever Windows app you start through the command line + a script. No other graphical application would be running at this point other than X, wine and the app. :P

I don't have a clue how to do this (starting X, then an X app inside it).

Or run a really lightweight window manager when running heavy games.

---

### Post by Thelasko on 2008-10-06
> **DaVince21 said:**
> You know what would increase performance most? Shutting down *any* graphical session and purely run an X session for whatever Windows app you start through the command line + a script.
Umm, maybe I missed something, but I thought that was what we were talking about here.  Most of these scripts have options to shut down the graphical sessions.

For example, [this script]("http://ubuntuforums.org/showpost.php?p=3908174&postcount=2") opens a new xserver session, the original one is in RAM/Swap and therefore uses no video resources.  However, if you uncomment the line that says:
```
#sudo /etc/init.d/gdm stop
```
you will completely close your original xserver session, saving massive amounts of system resources.

---

### Post by luposolo on 2008-10-06
the problem when i use this script [http://ubuntuforums.org/showpost.php?p=3908174&postcount=2](http://ubuntuforums.org/showpost.php?p=3908174&postcount=2), it launchs the x server but not the application all i get is a cursor with a X on it and a black screen in the background the application does not launch and i did typed in the right directory

---

### Post by luposolo on 2008-10-06
nvm i got it to work

---

### Post by Thelasko on 2008-10-06
> **luposolo said:**
> nvm i got it to work

What did you do?  Others may learn from this...namely me!:)

---

### Post by luposolo on 2008-10-06
well i was using a launch script before and it didnt work so instead of using the launch script i just copy and pasted the code in the console of course i changed the directory as needed

---

### Post by rovae on 2008-10-06
Be sure to use styling tools specially made for [Lace Wig](http://www.royalmewigs.com) such as a wig styling comb, wig brush or wig pic comb.  CAUTION:  When styling synthetic [Lace Wigs](http://www.royalmewigs.com) never use heating styling tools on your wig or expose your [Full Lace Wigs](http://www.royalmewigs.com) to excess sources of heat such as:  hair dryers, curling irons, open ovens, boiling water, barbecue grills and even some cigarette lighters, because the heat will damage the fibers.  When styling [Human Hair Wigs](http://www.royalmewigs.com/lace-human-hair-wigs-c-10.html) you can use all the tools you have used on your own hair (hair dryer, curling iron, hot rollers) and do not need to worry about heat exposure, but must use products especially formulated for [Lace Front Wigs](http://www.royalmewigs.com/lace_front_wigs.html).

---

