---
title: "Quake 3, no sound, im going bonkers! help!"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by lucky2 on 2007-04-29
OK, ive tried most evreything I can think of, and am left with, I think, one option.. To re-compile the kernel including support for my sound hardware, which is via onboard sound 8237A southbridge HD Audio or similar. Im using Ubuntu 6.10 amd64, can someone point me towards the kernel patch I need, and some guides please as I've never done this before. thanks

---

### Post by stmiller on 2007-04-29
Are you using the newest ioquake for 64bit? 

[http://ioquake3.org/](http://ioquake3.org/)

---

### Post by lucky2 on 2007-04-29
arg! :D I should of put in the post that I need to get vanilla quake working because I would like to play online on servers with punkbuster enabled.

---

### Post by Kilz on 2007-04-29
> **lucky2 said:**
> OK, ive tried most evreything I can think of, and am left with, I think, one option.. To re-compile the kernel including support for my sound hardware, which is via onboard sound 8237A southbridge HD Audio or similar. Im using Ubuntu 6.10 amd64, can someone point me towards the kernel patch I need, and some guides please as I've never done this before. thanks

Do you have sound in other things. Do you hear sounds when you go to System >Preferences > Sound and click the play button next to the login sound?

---

### Post by Stickymaddness on 2007-04-30
I've got the same problem. Using Feisty and sound is via onboard sound on a nforce mobo. The game runs beautifully otherwise, so I'd really love to get the sound working!!

My sound does work fine everywhere else....

---

### Post by ghandi69_ on 2007-04-30
Just thought I'd chime in... I had this exact same problem about 3 months ago.  However, I never got it working... EVER!!!

My sound works perfectly fine using the same install process for other ID games, such as Doom3 and Quake4.  Quake3 however is a no go.

---

### Post by strumluff on 2007-04-30
run this command as root then start the game:

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

if that fails try:

echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

Then again the 64 executable may be named differently so name the quake3.x86 to whatever the executable for the game is for 64bit.

That got my sound working, only problem I have with the game is that I can't play online because it gets stuck at Awaiting snapshot...

If you can help me with that one then we'll be even :P

---

### Post by lucky2 on 2007-04-30
** Warning! , contains annoying solution that requires purchase of a new sound card Danger Will Robinson!!I ** I should of posted but I've been playing Qquake 3 ;) . I can only assume that this solution will work for everyone having no sound 'just' in quake 3 and such. I gave in and turned off the onboard (via 8237 HD Audio) and just plugged in my trusty old SBLIVE that I was using in the other room, rebooted, works like a charm. SBLive's are going for 5quid on Auction Sites (one in 15 minutes! :D), thing is now I know the computer in the lounge has non-working onboard sound now instead :(... to the Auction Site!!!! :) >>>

---

### Post by Sockerdrickan on 2007-05-01
Install libopenal

---

### Post by Stickymaddness on 2007-05-02
> **strumluff said:**
> run this command as root then start the game:

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss



You rawk! My Q3 has sound!! I'd been going crazy trying to get the sound working!! What exactly have I done with that command?

Edit:

How can I make that command "stick" so I can just run quake from a shortcut, without having to first open a terminal, sudo -i and then enter the command?

---

### Post by Stickymaddness on 2007-05-02
Looks like I spoke too soon :(

The sound only works in the menu and in q3dm0. Anything else and the game freezes :confused: 

I also tried installing libopenal, which didn't help...

---

### Post by strumluff on 2007-05-02
> **Stickymaddness said:**
> Looks like I spoke too soon :(

The sound only works in the menu and in q3dm0. Anything else and the game freezes :confused: 

I also tried installing libopenal, which didn't help...

Well that is odd that the menu and 1 map works but nothing else. I have rooted around for other solutions and you can try editting the pak0.pk3 file within the baseq3 folder and deleting the music folder and try the game then to resolve the freezing issue. The only thing here is you won't be able to play on pb enabled servers.

---

### Post by Nehvrook on 2007-05-11
Hi, I'm having the same problem as OP. Quake 3 runs fine but there is no sound. i tried running those commands you said but it says permission denied (Even though I put sudo in front) can anyone help me?

---

### Post by RawMustard on 2007-05-11
I've never had sound work in Quake3 in any Ubuntu since the first version, with many different sound cards.  Oh I did once in dapper using jack, but the sound had a lot of static I never could solve.

Maybe this [link]("http://ubuntuforums.org/showthread.php?p=1215205#post1215205") will help

---

### Post by strumluff on 2007-05-11
> **Nehvrook said:**
> Hi, I'm having the same problem as OP. Quake 3 runs fine but there is no sound. i tried running those commands you said but it says permission denied (Even though I put sudo in front) can anyone help me?

You need to run the commands in the root terminal, not sudo in a normal terminal. You can start root terminal by going Applications -> System Tools -> Root Terminal. If its not there you can enable the item from System -> Preferences -> Menu Layout.

---

### Post by ghandi69_ on 2007-05-11
> **strumluff said:**
> Well that is odd that the menu and 1 map works but nothing else. I have rooted around for other solutions and you can try editting the pak0.pk3 file within the baseq3 folder and deleting the music folder and try the game then to resolve the freezing issue. The only thing here is you won't be able to play on pb enabled servers.

Same thing happened with me.  Running the command made the sound work in the menu, but playing the game with that command always resulted in a freeze.

---

### Post by strumluff on 2007-05-11
2 more ideas for you then.

See what happens when you run this before you start the game:

```
sudo chmod o+r /dev/dsp
```

Also at the bottom of this guide is some information on using q3jack, if it works for you please report back :)

See Section 6 here: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games")

---

### Post by Nehvrook on 2007-05-13
I've  tried all of the suggestions above, including the jack one, and I STILL have no sound :(
After trying the command "echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" the system just locked up. All the others allowed Quake to run but there was no sound still

Edit, I got sound working in the menu but the game crashes as soon as I enter a map just like Stickymadness. Anyone got a solution for this?

---

### Post by Nehvrook on 2007-05-13
> **strumluff said:**
> Well that is odd that the menu and 1 map works but nothing else. I have rooted around for other solutions and you can try editting the pak0.pk3 file within the baseq3 folder and deleting the music folder and try the game then to resolve the freezing issue. The only thing here is you won't be able to play on pb enabled servers.


This man hit the nail on the head :P I now have sound working fully in Quake III

Go to wherever you installed Quake III (For me this was /home/lee/ProgramFiles/Quake3) and in that folder find the baseq3 folder. Inside there will be a bunch of archive files. Using the archive manager (comes with Ubuntu) open the one called pak0.pk3 (You'll have to change the permissions to let you read and write to this file) and find the music and hit delete. (I made a backup of pak0.pk3 (Just copy it somewhere else on your hard drive in a folder called backup or something) just incase)
Once you've deleted the music close the archive manager and go to the root terminal. In the root terminal type in
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
hit enter then type in
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
and hit enter
Then point the terminal at your quake 3 file (For me this was /home/lee/ProgramFiles/Quake3/quake3) and it will launch the game with sound and it shouldn't crash when you load maps

This works for me, other people seem to be having problems with static and stuff, so I'm not sure if it'll work for everyone. Thanks for all the help in this thread, I got there in the end XD


EDIT: Just thought I'd link to this thread [http://ubuntuforums.org/showthread.php?p=2646720#post2646720](http://ubuntuforums.org/showthread.php?p=2646720#post2646720) 
Someone helped me make a launcher icon so you don't have to enter this code every time you want to play the game

---

### Post by Stickymaddness on 2007-05-14
Awesomeness! 

I've just finished my first Ubuntu game of Q3 with sound!! Thanks to everyone who helped!! =D>

---

### Post by strumluff on 2007-05-14
Glad I could be of service. It's just a shame that this solution does not allow you to play on punkbuster enabled servers.

---

### Post by MikeReiner on 2007-05-14
> **strumluff said:**
> Glad I could be of service. It's just a shame that this solution does not allow you to play on punkbuster enabled servers.

That more or less completely destroys the value of this fix to me. :( There has GOT to be a way to get this working without modifying the .pak files..

---

### Post by Stickymaddness on 2007-05-15
Ok this is a little off topic, but how do you guys find quake in linux compared to in windows? For me I find that it's allot less smooth in linux, esp with regards to how quickly it responds to keyboard and mouse activity!

---

### Post by strumluff on 2007-05-15
I know it destroys the value of the fix because of that but it's the only fix! Sucks I know, but thats why I have an XP partition just for gaming.

I find it just as smooth in linux though as in windows. I cap both at 125fps and both run without problems not surprising though as I'm using an Nvidia 6600GT.

The reason you may be finding the game choppy could be because of the drivers you are using in linux?

---

### Post by Stickymaddness on 2007-05-15
By choppy I don't mean graphical performance. Graphically the game runs fine and I can't see any difference at all. 

I mean your actual movement in the game, it seems slower than in windows... The way you move around or jump just seems very different and not as smooth.

As for the punk buster bit, as far as I can see I can still join punk buster enabled servers?

---

### Post by strumluff on 2007-05-15
If you didn't edit the pak0.pk3 to remove the music folder then playing on a pb server should be fine.

Personally, I don't find any difference between playing on the two Operating Systems with similar config layouts. Your movement may be affected by the resolution you use or by the cg_fov value

---

### Post by Stickymaddness on 2007-05-15
I did have to edit pak0.pk3 to get my sound working and as far as I can see I can still connect to punk buster servers!

My res and cg_fov value are the same in both....maybe it's just me, but it seems very different....

---

### Post by strumluff on 2007-05-15
Well I guess the reason for that is the configurability of punkbuster. Theres a couple of servers I play on that check for changes of your game files, and ofcourse it finds the change in the pak0.pk3 file and doesn't allow joining the server.

It will be interesting to see if anyone else finds it different. I would have thought, if anything native game performance in linux would be better than windows.

---

### Post by Nehvrook on 2007-05-16
> **Stickymaddness said:**
> Ok this is a little off topic, but how do you guys find quake in linux compared to in windows? For me I find that it's allot less smooth in linux, esp with regards to how quickly it responds to keyboard and mouse activity!

It runs exactly the same for me. Neither better nor worse. It ran perfect on Windows and it runs perfect here lol

---

