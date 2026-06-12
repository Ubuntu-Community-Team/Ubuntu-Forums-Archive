---
title: "Having a few issues with Swiftdove"
date: 2007-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angelbeast on 2007-09-23
I just discovered swiftdove and it sounded good so i installed it. But alas i am having a few issued with it.

1. I had the AdBlock extension installed on it and each time it starts up it says adblock is missing.

2. If i have it checked in the prefs to check to see if it is the default email client the little box to MAKE it default pops up every time it's started. Also with this if i hae it checked to be the default for feeds and newsgroups it seems to forget this when it is closed and restarted.

3. If i am in Swiftweasel and click on sendlink in the file menu it opens the main program insteadof just a compose window.

And lastly (i think)...

4. when i go to the help menu in swiftdove and click on get help or whatever it is it opens up a whole new and seperate Swiftweasel window.

Okay so has nyone else used toe latest version of this and had the same issues? If so can they be fixed? I AM runing the AMD 64 bit version.

*wonders where the great and mighty Kilz is who knows all*

---

### Post by Angelbeast on 2007-09-23
I also just found out that when i reply to a message it quote it TWICE...

I wonder if this is even worth bothering with...

---

### Post by Kilz on 2007-09-23
> **Angelbeast said:**
> I just discovered swiftdove and it sounded good so i installed it. But alas i am having a few issued with it.


*wonders where the great and mighty Kilz is who knows all*

I dont know all. But my experience is different than yours. Do you have thunderbird installed as well as swiftdove?

---

### Post by Angelbeast on 2007-09-23
> **Kilz said:**
> I dont know all. But my experience is different than yours. Do you have thunderbird installed as well as swiftdove?

*LOL* yes different as in MORE of it...I'm learnimg ore and more but you are still like Yoda to me and i'm always grateful for your help :-P

And i do indeed have thunderbird installed..I had uninstalled it initially when i firt installed swiftdove but then i noticed that in the 'prefered pps' window in the ubuntu administration mnu it aid something like /home/ron/Swiftweasel/Thunderbird/ so i guessed that it needed thunderbird somehow so iput it back on...

and i also noticed that the openeing a new window issue happen also when you click on a link inside an email...

---

### Post by Angelbeast on 2007-09-23
Oh and the adblock problem is all taken care of...that ws just an incompatability with another extension *LOL*

---

### Post by paradoxni on 2007-09-23
Have you checked in you Ubuntu menu: System > Preferred Applications.

Webbrowser - Custom
Command - ```
swiftweasel %s
```

Mail reader - Custom
Command - ```
swiftdove %s
```

These work fine for me.

---

### Post by Kilz on 2007-09-23
Just curious, what version of the 6 did you install? Also did you install a deb file or the tarball?

---

### Post by Angelbeast on 2007-09-23
> **paradoxni said:**
> Have you checked in you Ubuntu menu: System > Preferred Applications.

Webbrowser - Custom
Command - ```
swiftweasel %s
```

Mail reader - Custom
Command - ```
swiftdove %s
```

These work fine for me.

Well would you believe that was the problem? For some reason when i installed Swiftdove it put in the command line in the prefered apps '/home/ron/Swiftdove/Thunderbird/" i THOUGHT that seemed a little strange but i just figured it meant that it depended on thunderbirb in some way so i put tb back on...

NOW if i could just grasp how to compile thingsfrom source haha...

thanks both for your help...

Hey i just watched that documentary about open source and linux called Revolution...it was pretty good...you guys see it?

---

### Post by Angelbeast on 2007-09-23
Alright possibly i spoke too soon...the command worked fine so i took off thunderbird again...but when i restarted swiftdove the prefered apps setting went back to this: 

"/usr/local/swiftdove/thunderbird "%s""

wht do i do about that??  *LOL*

---

### Post by paradoxni on 2007-09-23
change it back? :)

---

### Post by Angelbeast on 2007-09-23
> **paradoxni said:**
> change it back? :)

*LOL* i did change it back \\:D/

so does that mean everytime i close swiftdove and open it to use it again i have to do that? well what a pain *LOL*

---

### Post by paradoxni on 2007-09-23
ive no idea why its doing that..its fine here :(

---

### Post by Kilz on 2007-09-23
I think its because you are installing or uninstalling thunderbird, not simply closing swiftdove.

---

### Post by Angelbeast on 2007-09-23
> **Kilz said:**
> I think its because you are installing or uninstalling thunderbird, not simply closing swiftdove.

I have TB completely uninstalled...Profiles and root folder and all...It's just Swiftdove...The TB folder doesn't even ext on my machine anymore *LOL* ... Still when i close out swift dove the setting in prefered apps changes bck to usr/local/swiftdove/thunderbird etc... and when i go right into the folder that it says right there there/s nothing at all that says thunderbird...

---

### Post by Angelbeast on 2007-09-23
okay it's makin a liar out of me again...it looks like when i don't have it check to see if it's the default mail client then it works okay...is that just some sort of bug or is there some way to fix that?

---

### Post by paradoxni on 2007-09-24
just leavae it unticked, thats how  mine is and works fine.

---

### Post by drs305 on 2007-09-24
I have started using Swiftdove and Swiftweasel and they either use the same folders as their original counterparts or cloned them. If I uninstall Firefox and Thunderbird, will the profile folders remain even if they are located within the Firefox/Thunderbird folders? 

My Firefox profile is in a separate folder in my home but the Thunderbird profile is nestled in the folder created when I set up the program. Do I need to copy these profiles elsewhere before the uninstall (notwithstanding safe backup procedures)?

---

