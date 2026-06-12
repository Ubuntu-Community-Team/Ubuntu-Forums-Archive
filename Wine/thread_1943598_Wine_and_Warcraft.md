---
title: "Wine and Warcraft"
date: 2012-03-19
forum: Wine
---

### Post by Crossbow on 2012-03-19
[edit: solved this part by accident, since no one here would help me.]

Current problem: Game periodically goes black and stays that way until I give up and shut down. 

I'm running 11.04 and wine 1.2.2, which is the only version in my software center. My machine is a Dell Inspiron 530.

Graphics card:
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8300 GS] (rev a1)

---

### Post by Crossbow on 2012-03-19
[disregard]

---

### Post by Perfect Storm on 2012-03-20
Moved to Wine forum.

---

### Post by Crossbow on 2012-03-20
Well, I know you'll all be thrilled to hear that I got the game working. I don't know how. I just kept reinstalling it until it worked. Now it runs but I don't have video. I don't know if this is a wine problem. Probably not. I don't even know what to check. I have the current version of Nvidia. 

I have audio. I keep hearing fights going on around me. If you see a female tauren wandering around the game walking into walls and shooting at trees, don't worry, that's just me. 

I tried to ask for help on the game forums but it claims I don't have a character. :/

Anyway. This was just moved from the "absolute beginner" forum to the Wine forum, but I have no idea if it's a Wine problem or not. Well, it probably is - I probably shouldn't be drinking $5 wine while doing this.

---

### Post by cwwilson721 on 2012-03-20
Search this forum for "wow+wine", and 99.99% of your answers are there.

Plus, read the stickies on the top of this forum, esp "How to get help"...

---

### Post by Crossbow on 2012-03-20
First, I didn't even know this particular forum was here. It is not listed in the "how to get support" thread. I posted this in "absolute beginners" and it was moved here by a moderator. Second, searching wine+wow was the FIRST thing I did. If my question had been that obvious, I wouldn't have started a thread. If you think my answer is very obvious, ***please*** link me to it.

I still don't even know if this is a Wine problem or an Nvidia problem. If someone could even tell me that much it would be a big help.

---

### Post by cwwilson721 on 2012-03-20
Either way, SEARCH THIS FORUM (Link on top of this forum in drop down box), and READ THE STICKIES.

And yes, your answer is there, believe it or not.

This is purely a volunteer effort in here. Just because you don't want to, or think you need to search, it doesn't mean we will answer the exact same question over and over and over and over and over.

I already have a VERY good idea what the issue/fix is. But it is covered in the install.

---

### Post by Crossbow on 2012-03-20
I didn't say I didn't want to or didn't need to search. I said that I DID search and didn't find what I need. If you did, fantastic. Feel like sharing? 

I read the Wine install. I read the WoW install. I said so in my original post. (I finally got them installed and deleted that part of my post.) 

I know this is volunteer, so if you don't want to help, I don't know why you are not reading what I wrote. Telling someone to go back and redo everything they just said they did is not helping, it's condescending. If you don't want to help, don't help, but don't sit here and lecture me without even reading what I said.

(edit)

For example: I found this: [http://ubuntuforums.org/showthread.php?t=1755909&highlight=warcraft+black](http://ubuntuforums.org/showthread.php?t=1755909&highlight=warcraft+black)

but I am not running dual monitors. 

I found a lot of threads about no image at all, but that's not the problem I am having.

---

### Post by cwwilson721 on 2012-03-20
Again: READ THE STICKIES!

Then, post back here.

Need:
[LIST]
[*]Hardware
[*]Wine Version
[*]Are you running in OpenGL or D3D?
[*]What else have you installed into wine?
[*]What mode is wine running? (XP, Windows 2000, Windows 7?)
[/LIST]

So, READ THE STICKIES, and THEN post.

I'm not condecending, I'm trying to help. But if you DON'T READ, I won't help.

Your choice. 

If you WOULD have read the stickies, you would have already posted the info, and you would have gotten an answer.

---

### Post by Crossbow on 2012-03-20
The version of wine I'm using ***is*** in my original post. So is my computer model. So is my graphics card. How can you accuse me of not reading this stuff when you didn't even read the post you're whining about? 

As for what's not there: I tried it with both XP and 7 modes. I have no idea what OpenGL means. 

Doesn't matter. I did a search on Google instead of this forum and found the answer right away. 

In the time it took you write your very first comment on here, you could have more easily just linked me to whatever thread it is that you believe explains the problem. And now you're about to say that that wouldn't "teach" me to search, except I've already said three times that I did search, and even clicked on the search link you provided and did not find whatever it you think I'm supposed to find. So the only thing you've "taught" me here is that I should just search Google instead of the forums in the first place. So, thanks.

---

### Post by cwwilson721 on 2012-03-21
And you learned...?

Nothing.

But your last post spoke volumes.

"opengl" is the answer. 

IF you actually searched, and IF you actually followed almost EVERY post out there about installing wow/wine, "-opengl" is there.

For the future:
Here's an example of how you SHOULD have started:```

Ubuntu 11.04 and wine 1.2.2
Graphics card:
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8300 GS] (rev a1)
Installed proprietary drivers
Using D3D

Skimmed install instructions, and picked and chose what I wanted to do. 

Now I have mostly "black" screen.
```

Answer: ```
Install wine ppa/wine 1.3 (in stickies on top of forum)
Use "-opengl" (Either append to end of launch command, or edit config.wtf in WoW install. Instructions posted everywhere in this forum)
Use XP as wine OS (Will help a TON with sound and patch issues)
DO NOT BOTHER WITH D3D on "underpowered" graphics (83300GS is real low-end, even in WoW now)
```

See how much easier that is? I WAS trying to help, but, as when you installed WoW, you didn't follow along.

Just trying to help.

Next time, you'll save yourself alot of aggravation. Post hardware (not model #. We aren't going to look it up), drivers, Ubuntu ver, wine ver, and what you did.

---

